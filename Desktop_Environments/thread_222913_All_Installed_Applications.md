---
title: "All Installed Applications"
date: 2006-07-25
forum: Desktop Environments
---

### Post by visvak on 2006-07-25
is there any way i can get a list of all my installed apps in atext file or something ? i'm planning to move to a new pc and would like to reinstall all of them there. i'mm not backing up because i've heard backup horror stories where unrelated stuff is installed/not installed.

---

### Post by llamakc on 2006-07-25
You can get a list of packages installed with:
From: [http://www.debian.org/doc/manuals/reference/ch-package.en.html](http://www.debian.org/doc/manuals/reference/ch-package.en.html)
**6.4.9 Record/copy system configuration**

   To make a local copy of the package selection states:  
     $ dpkg --get-selections "*" >myselections   # or use \*
  "*" makes myselections include package entries for "purge" too.  
 You can transfer this file to another computer, and install it there with:  
     # dselect update
     # dpkg --set-selections <myselections
     # apt-get -u dselect-upgrade    # or dselect install

---

### Post by aysiu on 2006-07-25
```
dpkg -l > textfile.txt
``` should do it.

---

### Post by llamakc on 2006-07-25
> **aysiu said:**
> ```
dpkg -l > textfile.txt
``` should do it.

Yep, `dpkg -l > some.file` works perfectly but to then reinstall from there you'd have to start awk'ing out the package names for reinstallation. dpkg has a builtin ability with the --get-selections/--set-selections flags that makes moving one package set from computer A to computer B really simple.

---

### Post by visvak on 2006-07-26
thanks for all the help. i got what i was looking for.

---

