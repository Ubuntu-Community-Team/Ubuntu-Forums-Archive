---
title: "how come I cant open shell scripts?"
date: 2006-01-02
forum: General Help
---

### Post by taseal on 2006-01-02
I just installed superkaramba (sp?) and I keep clicking on configure and the file will not open... I also downloaded a icon set and it says to open the buildlist (which is a script as well) and it will not open!

how do I open this :(

thx

---

### Post by gsdefender on 2006-01-02
Maybe because shell scripts require the use of an external application - a terminal emulator - to be shown in XWindows. I don't know what's the default behaviour in KDE since the last release I used was KDE 1.1, but I would open konsole, then cd to the directory you've extracted the files to, then ./configure.

---

### Post by taseal on 2006-01-02
yup, that worked... thx!

how do u go back a directory in terminal? not cd..

---

### Post by gsdefender on 2006-01-02
I don't know if I have well understood, but I would do:

**pushd .  **                         

or

**pushd /home/taseal/files**

if I wished to save a specific directory, then

**cd /some/other/place**

when finished, I would do

**popd**

to come back there.

Just remember that pushd/popd entries are stored first-in last-out: you need to use popd twice if you have saved

/ /home

in this order and you need to go back to /. Pushd without any parameter won't do anything, also.

---

