---
title: "Kde 3.4.2: causes new problem with konqueror"
date: 2005-08-01
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-08-01
Hi

I updated to kde 3.4.2 and today i found that konqueror has trouble entering folders that contain the characters '[' or ']'. 
For example...create one of these two folders and you will see that you will have trouble entering them in konqueror.

[list]adf[][/list] 
[list]as[[/list]

Then remove the brackets and they will work fine. Anyone that can think of a solution to this problem? I have many directories that contain brackets and I don't want to change.

---

### Post by ghostintheshell on 2005-08-02
yes, I have the same issue.

this is a bug and it's already known --> [http://bugs.kde.org/show_bug.cgi?id=107170](http://bugs.kde.org/show_bug.cgi?id=107170)

cheers.

---

### Post by yongyi on 2005-08-02
I have the same issue,too.

---

### Post by geearf on 2005-08-03
same here.

---

### Post by geearf on 2005-08-04
the updates I had yesterday for .2 (new ones) did not change this :(

---

### Post by daller on 2005-08-04
Well, I am probably considered an idiot, asking this question, but how did you get 3.4.2???

---

### Post by Roptaty on 2005-08-04
[QUOTE=daller]Well, I am probably considered an idiot, asking this question, but how did you get 3.4.2???[/QUOTE]
 Add the following to your apt/sources.list
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

---

### Post by ghostintheshell on 2005-08-04
[http://www.kubuntu.org/hoary-kde-342.php](http://www.kubuntu.org/hoary-kde-342.php) ;)

cheers.

---

### Post by JLTB on 2005-08-04
same prob.

if you go up to the address bar and change "......../blahblah[]" to "......../blahblah[]/" (put a slash at the end) and hit enter it will go in just fine.

---

### Post by ghostintheshell on 2005-08-04
[QUOTE=JLTB](...)

if you go up to the address bar and change "......../blahblah[]" to "......../blahblah[][color=Red]**/**[/color]" (put a slash at the end) and hit enter it will go in just fine.[/QUOTE]

yeah, it works! thank you man!

---

### Post by yongyi on 2005-08-04
[QUOTE=JLTB]same prob.

if you go up to the address bar and change "......../blahblah[]" to "......../blahblah[]/" (put a slash at the end) and hit enter it will go in just fine.[/QUOTE]
well done!

---

### Post by samwyse on 2005-08-05
Is it going to be patched or do we have to wait for KDE 3.4.3? :?

---

### Post by geearf on 2005-08-05
Maybe the patch will be .3 in fact.

---

### Post by drizek on 2005-08-05
[QUOTE=geearf]Maybe the patch will be .3 in fact.[/QUOTE]
 AFAIK, there is not .3.

---

### Post by geearf on 2005-08-05
how do you know ?

---

### Post by GoldBuggie on 2005-08-07
The bug seems to have gotten the status fixed ([http://bugs.kde.org/show_bug.cgi?id=107170)](http://bugs.kde.org/show_bug.cgi?id=107170)). Let's hope this reaches Kubuntu soon so I don't have to compile it myself.

---

