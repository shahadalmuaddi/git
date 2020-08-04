<div dir="rtl" align="right" >
    
 ##  اضافة التغييرات الى git
 
 </br>
 
في هذة المرحله يجب ان يكون لديك نسخه خاصه بك من git repository و نسخه من جميع ملفات مجلد المشروع في جهازك الشخصي . وبالطبع ستحتاج الى اجراء تعديلات على ملفاتك حتى تصل الى مرحلة تريد فيها ان ترى مالذي تم تغييره او حفظة بالفعل وياتي دور  git  الان حيث تقوم بتصنيف حالة ملفاتك الى احد هذه الحالتين إما tracked او untracked.عندما تكون حالة الملف tracked معنى ذلك ان git تقوم بمراقبه هذا الملف وجميع التغيرات التي تحصل عليها من قبلك ويندرج تحتها ثلاث حالات ايضا : الاولى modifide تعني انك قمت باجراء تغيير على الملف بعد اخر مره تم حفظ الملف فيها ، الثانية unmodified لا توجد تغييرات على الملف بعد , و الاخيرة staged تم حفظ التغييرات ولكن لم يتم تنفيذ امر commit . والحاله الثانيه untracked هي حالة جميع الملفات التي لم يتم متابعتها بعد من قبل git ولكنها موجوده في مجلد المشروع الخاص فيك.

</br>

ملاحظة 💡 
بالبداية تكون جميع الملفات داخل المجلد بعد امر `clone` في حالة  tracked and unmodified الى ان تقوم بالتعديل على احد هذة الملفات فتتغير حالته الى modified بعد ذلك تقوم باضافته الى مرحلة staged واخيرا يتم حفظه باستخدام امر commit

</br></br>

<p>    
    
![img1](https://user-images.githubusercontent.com/68843051/89102092-86895800-d40e-11ea-93d6-1e9526f05d04.jpg)

</p>


</br></br>


###  استعراض حالة الملفات  

</br>

اولا لابد من التاكد بانك موجود داخل مجلد المشروع قبل البدء بتنفيذ الاوامر ثم نقوم باستعراض حالة الملفات باستخدام الامر `git status ` هذا الامر يقوم باستعراض جميع حالات الملفات الموجوده وايضا يخبرك باسم التفرع bransh الذي تعمل عليه 

</br>

 المخرجات 

<div dir="ltr" align="left">

```
 Dev: git status
On branch master
Your branch is up to date with 'origin/master'.
```
</div>

</br>
كما هو موضح بالمخرجات لايوجد اي ملف غير متابع او اي تغييرات حاصله في الملفات .

</br></br>

### متابعة ملف جديد

</br>

سنقوم الان باضافة مجلد جديدة واستعراض حالة الملفات سوف تكون حالة الملف الجديد غير متابع من قبل git  ويندرج تحت عنوان  “Untracked files” فلذلك سنستخدم الامر` git add` لنقله للمرحلة التاليه وهي staged لتخبر git بالبدأ في متابعة هذا الملف وجميع التغيرات اللتي تحدث له وايضا من ميزات هذة المرحلةانها موجوده كي يقوم المستخدم باختيار الملفات اللتي يريد حفظها والتاكد من عدم حفظ ملفات او التغييرات بشكل خاطئ باستخدام commit .

</br>


<div dir="ltr" align="left">

```
Dev: git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	app.js

nothing added to commit but untracked files present (use "git add" to track)

```
</div>


<div dir="ltr" align="left">

```
Dev: git add app.js
Dev: git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   app.js

```
</div>

 </br>
  
كما هو موضح في المثال ملف app.js الان في مرحلة staged لانه موجود تحت "Changes to be committed"  

</br>
</br>

### اضافة  ملف معدل الى staging area

</br>

عند حدوث اي تغيير في الملف  فيجب اضافة هذه التغييرات الى staging area عن طريق تنفيذ امر ` git add` . مثال على ذلك سنقوم الان باضافة تغييرات على  file-stages.md  ونستعرض حالة git 

</br>


<div dir="ltr" align="left">

```
Dev: git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   app.js

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file-stages.md


```
</div>

</br>

 في هذا المثال بعد اضافة تغييرات ظهر الملف تحت "Changes not staged for commit"  وحالته هي modified اي تم اجراء تغييرات لم يتم نقلها لمرحلة stage لذلك نستخدم امر `git add `لاضافة هذه التغييرات .اذا امر `git add` له عدة  استخدامات اما ان يستخدم لمتابعة ملف جديد او اضافة تغييرات حدثت للملف ايضا تعتبر كحفظ جزئي للعمل ولكن لم يتم عمل `commit ` بعد لتخزينها في history

</br>
 
 <div dir="ltr" align="left">

```
Dev: git add file-stages.md
Dev: git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   app.js
	modified:   file-stages.md


```
</div>

</br>

ملاحظة💡 اذا قمت باجراء اي تغييرات اخرى على الملفات الموجوده في مجلد المشروع يجب عليك تنفيذ امر `git add `لاضافة هذا التعديل الى باقي التغييرات  في مرحلة stage 
 
 </br>
 </br>
 
###  Short status 

</br>

اذا اردت استعراض حالة الملفات ولكن بشكر مختصر يمكنك استخدام الفلاق  s  مع الامر `git status`  ويتم تمثيل الحالات برموز معينه 
  - ?? تدل على الملفات الجديده 
  - A للملفات الجديده المضافه في staged area 
  - M للملفات المعدله 

</br>

<div dir="ltr" align="left">

```
Dev: git status -s
A  app.js
M  file-stages.md
```
</div>

</br>
</br>

### Ignoring Files

</br>

عندما يكون لديك ملفات لا تريد ان تكون متابعة باستخدام git وتريد ان تكون  مخفيه فيمكنك انشاء ملف .gitignore وتكتب بداخله اي ملف تريد ان يكون مخفي وغير متابع او يمكنك ان تكتب قاعده باستخدام regular expresión تقوم باخفاء الملفات اللتي تتطابق مع  هذه القاعده .

</br>

 <div dir="ltr" align="left">

```
#  a تجاهل كل ملفات بامتداد 
*.a

# استثني هذا الملف من القاعده الاولى 
!lib.a

#  app.js تجاهل ملف  
app.js
```
</div>

</br>
</br>

### استعراض staged area and unstaged changes

</br>

اذا اردت معرفة التغييرات اللتي اجريتها ولم تقم بعد باضافتها الى staging area يمكنك تنفيذ الامر `git diff`سيقوم باستعراض جميع ما تم اضافته او حذفه عن طريق عمل مقارنه بما هو موجود بالفعل في staging area والتغييرات اللتي لم تضف بعد ولكن لن يتم عرض اي شي اذا كانت جميع التغييرات موجوده بالفعل في داخل staging area

</br>

 <div dir="ltr" align="left">

```
% git diff         
diff --git a/lib.js  b/lib.js 
index e69de29..c989436 100644
--- a/lib.js    
+++ b/lib.js    
@@ -0,0 +1 @@
+consoul.log(hi")
\ No newline at end of file

```
</div>

</br>
</br>

### Commit 

</br>

بعد اضافة جميع الملفات والتغييرات اللتي تريد لمرحلة staging area الان يمكنك حفظ هذة التغييرات في داخل history المشروع باستخدام امر `git commit`
  * `git commit -m "your massage "` هذا الامر يقوم بالحفظ واضافة المسج المكتوبه بعد فلاق m كعنوان 
  * `git commit -v`هذا الفلاق يقوم بشرح التغييرات بشكل تفصيلي واستعراضها في محرر 
  * `git commit -a -m "your massage "` فلاق a يستخدم اذا اردت تجاهل الحفظ في staging area وحفظ التغييرات بشكل مباشر داخل  history المشروع 
  
  </br>
  
ملاحظة💡 عندما تقوم بتنفيذ امر `git commit ` او `git commit -v` فسيفتح لك المحرر لتقوم بالكتابه او التعديل وللخروج يمكنك الضغط على esc و كتابة :q والضغط على انتر 

</br>

 <div dir="ltr" align="left">

```
 
git commit -m "first commit massage" 
[master 6039f40] first commit massage
 3 files changed, 2 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 app.js

```
</div>

</br>

في المخرجات كما هو موضح يكتب اسم التفرع مع الرسالة والتغييرات اللتي حفظت 

</br>
</br>

### ازالة ملف 

</br>

عندنا تريد ازالة ملف من git لابد من ازالته ايضا من staging area ويقوم الامر `git rm`بهذا العمل 
* اذا كان الملف داخل staging area ولم تتمكن من حذفه يمكنك استخدام فلاق f لتنفيذ الامر  
* اذا اردت الاحتفاذ بالملف في جهازك ولكن يحذف من git يمكنك استخدام الامر `git rm --cached README”

</br>

 <div dir="ltr" align="left">

```
 % git rm app.js
rm 'app.js'
 % git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	deleted:    app.js


```
</div>

</br>

### تغيير اسم الملف 

</br>

git تمكنك من تغيير اسماء الملفات باستخدام امر `git mv old_file new_file`
<br>
<div dir="ltr" align="left">

```
$ git mv README.md README
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
```
</div>


 </div>

