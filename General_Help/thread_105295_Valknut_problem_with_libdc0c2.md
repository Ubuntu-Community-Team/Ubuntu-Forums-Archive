---
title: "Valknut problem with libdc0c2"
date: 2005-12-18
forum: General Help
---

### Post by LaMpiR on 2005-12-18
i have some problems with DCgui and i decided to install valknut which looks great by screenshots. I have downloaded valknut_0.3.7-2_i386.deb from packages.debian.org and when i tried to install it i got this error:
> 
lampir@ubuntu:~/Desktop$ sudo dpkg -i valknut_0.3.7-2_i386.deb
Password:
Selecting previously deselected package valknut.
(Reading database ... 98125 files and directories currently installed.)
Unpacking valknut (from valknut_0.3.7-2_i386.deb) ...
dpkg: dependency problems prevent configuration of valknut:
 valknut depends on libdc0c2 (<< 0.3.7-99); however:
  Package libdc0c2 is not installed.
 valknut depends on libdc0c2 (>= 0.3.7-0); however:
  Package libdc0c2 is not installed.
 valknut depends on libpng12-0 (>= 1.2.8rel-4); however:
  Version of libpng12-0 on system is 1.2.8rel-1ubuntu3.
 valknut depends on libqt3-mt (>= 3:3.3.5); however:
  Version of libqt3-mt on system is 3:3.3.4-8ubuntu5.
 valknut depends on libstdc++6 (>= 4.0.2); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing valknut (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 valknut

so automatically i've tried to install one by one lib but when i came to libdc0c2 i got this error:

> 
lampir@ubuntu:~/Desktop$ sudo dpkg -i libdc0c2_0.3.7-3_i386.deb
(Reading database ... 98251 files and directories currently installed.)
Unpacking libdc0c2 (from libdc0c2_0.3.7-3_i386.deb) ...
dpkg: error processing libdc0c2_0.3.7-3_i386.deb (--install):
 trying to overwrite `/usr/lib/libdc.so.0.0.1', which is also in package dclib
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 libdc0c2_0.3.7-3_i386.deb

Can somebody tell me why because i would realle like to use Valknut ?

---

### Post by raketti on 2006-05-06
Install valknut from the universe/multiverse/backports repository, that way you'll get all the dependencies installed too. :)

---

