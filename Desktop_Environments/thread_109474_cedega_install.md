---
title: "cedega install"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Akya on 2005-12-28
im trying to install cedega by following the linux-gamers.net howto and evey time i get to installing it by entering sh winecvs.sh it starts the screen and i get #1 on the list then i try to run it and it says

--------- Error log - file /home/******/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/*****/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by Ocxic on 2005-12-28
try installing wine

---

### Post by pharcyde on 2005-12-29
It looks like you dont have cvs installed.

try:
**apt-get install cvs**

Then follow the guide again.  Make sure you have all the files installed per their installation guide.  The only reason to use their shell script is if you wish to checkout the latest version of wine source or try and compile cedega for free.

---

