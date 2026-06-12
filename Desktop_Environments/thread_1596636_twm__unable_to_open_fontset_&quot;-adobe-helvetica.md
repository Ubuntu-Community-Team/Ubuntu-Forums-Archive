---
title: "twm:  unable to open fontset &quot;-adobe-helvetica-bold-r-normal--*-120-*-*-*-*-*-*&quot;"
date: 2010-10-14
forum: Desktop Environments
---

### Post by gregwm on 2010-10-14
that's what i get on one of my 2 new lucid boxen when i try to run twm (1:1.0.4-2ubuntu2) inside vnc4server (4.1.1+xorg4.3.0-37ubuntu2).  any idea how to fix this?  the xfonts packages are installed, and no problem with twm on the console.  and no problem with twm inside vnc4server on the other lucid box.  both were installed via netboot (minimal), both were fleshed out with apt-get lubuntu-desktop, though there were presumably inconsequential differences, on the one that works fine:```
apt-get install twm
apt-get install vnc4server xvnc4viewer
apt-get install lxde-core
apt-get install lubuntu-desktop
```on the one with the twm problem:```
apt-get install lxde-core
apt-get install lxde
apt-get install twm
apt-get install vnc4server xvnc4viewer
apt-get install lubuntu-desktop
```and other even less relevant differences

---

### Post by ddombrowsky on 2010-12-16
I ran across this problem today as well.  twm will not start and it gives a font error message.

From the looks of the google results this is an ancient bug that has come and gone over the past year.  It was reported here for fedora: [https://bugzilla.redhat.com/show_bug.cgi?id=509639](https://bugzilla.redhat.com/show_bug.cgi?id=509639).  The workaround is to execute it with a specific shell variable:
```
$ LANG=C twm
```and all is well.  I don't know what the root cause of the problem is, and would be interested to know.  X fonts have always been a mystery to me.

---

