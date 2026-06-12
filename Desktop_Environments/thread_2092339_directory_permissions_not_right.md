---
title: "directory permissions not right"
date: 2012-12-07
forum: Desktop Environments
---

### Post by dwlamb on 2012-12-07
I am having some strange problems with various sub-directories of my home directory.  This is the output 
```
$> ls -l Docs/OpenOfficeTemplates/
ls: cannot access Docs/OpenOfficeTemplates/PresentationBkgrounds: Permission denied
ls: cannot access Docs/OpenOfficeTemplates/Calc: Permission denied
ls: cannot access Docs/OpenOfficeTemplates/web: Permission denied
ls: cannot access Docs/OpenOfficeTemplates/KeyboardShortcuts: Permission denied
ls: cannot access Docs/OpenOfficeTemplates/Impress: Permission denied
ls: cannot access Docs/OpenOfficeTemplates/KeyboardShortcuts.: Permission denied
ls: cannot access Docs/OpenOfficeTemplates/Writer: Permission denied
total 0
d????????? ? ? ? ?            ? Calc
d????????? ? ? ? ?            ? Impress
-????????? ? ? ? ?            ? KeyboardShortcuts
d????????? ? ? ? ?            ? PresentationBkgrounds
d????????? ? ? ? ?            ? web
d????????? ? ? ? ?            ? Writer

```Yet, if I perform the same with sudo, this is the result
```
$> sudo ls -l Docs/OpenOfficeTemplates/
total 28
drw-r--r-- 2 daniel daniel 4096 Dec  7 11:58 Calc
drw-r--r-- 2 daniel daniel 4096 Dec  7 11:58 Impress
-rw-r--r-- 1 daniel daniel 2088 Dec  7 11:58 KeyboardShortcuts
drw-r--r-- 2 daniel daniel 4096 Dec  7 11:58 PresentationBkgrounds
drw-r--r-- 2 daniel daniel 4096 Dec  7 11:58 web
drw-r--r-- 3 daniel daniel 4096 Dec  7 11:58 Writer
```Unfortunately, this is prevalent in a number of directories for my production.
How can I go about fixing this mess?

If I

[LIST]
[*]sudo copy the sub-directories and their contents to a new directory
[*]sudo change the owner to myself [danie:daniel]
[/LIST]
I still end up with permission denied and the rows of question marks when I perform ls -l

---

### Post by pkadeel on 2012-12-07
This is because your folders do not have execute permission set
also post the output of ```
$> ls -l /Docs
```
If you do not get any permission error in that output then the following shall solve your problem
```

sudo chmod -Rv a+rwX,go-w /Docs/OpenOfficeTemplates

```

---

### Post by dwlamb on 2012-12-07
thanks for the input...  In clearing the execute parameter for a recursive command intended for all files, it was not realised it would hit the directories as well, producing this problem

---

