---
title: "Need help installing easyh10, or just finding the right package it depends on"
date: 2006-08-27
forum: Desktop Environments
---

### Post by BongoBob on 2006-08-27
Hello everybody. I recently found out about a program for linux called easyh10 which allows me to use my supposedly only works on windows iRiver H10 mp3 player within linux. I downloaded the .deb files from [here]("http://packages.debian.org/unstable/sound/easyh10"). But when I try to sudo dpkg -i it, it says this...
```
bongobob@RaptorBandito:~$ sudo dpkg -i easyh10_1.4-1_i386.deb 
(Reading database ... 101354 files and directories currently installed.)
Preparing to replace easyh10 1.4-1 (using easyh10_1.4-1_i386.deb) ...
Unpacking replacement easyh10 ...
dpkg: dependency problems prevent configuration of easyh10:
 easyh10 depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing easyh10 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 easyh10

```.

Can someone tell me where I can get the right version of libc6?

Thanks in advance.

-BongoBob

---

### Post by suziequzie on 2006-11-02
easyh10 should be in the repositories (if you have multi and universe enabled). Try running synaptic or just 

apt-get install easyh10   

in a console.  I found that worked for me.

---

