---
title: "Help connecting Sixaxis controller to PC"
date: 2015-12-23
forum: Gaming &amp; Leisure
---

### Post by tekkah56 on 2015-12-23
Hello and thank you for taking the time to read my post.
For the past day, I have been trying to connect one of my Playstation 3 controllers to my computer by following the steps posted on the official help page [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis) however I have run into a slight problem (two actually). My first problem is when I tried to run ```
patch -p1 < patch-hidd-3.19-pabr3
```
When I entered this code it showed me this dialoge in the terminal
```
big_daddy@BigDaddy-Aspire-V3-572P:~/bluez$ patch -p1 < patch-hidd-3.19-pabr3
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- bluez-utils-3.19/hidd/main.c.orig    2007-05-09 08:40:42.000000000 +0200
|+++ bluez-utils-3.19/hidd/main.c    2007-10-15 02:29:40.000000000 +0200
--------------------------
File to patch: 

```

After giving up on this I went on to the next step and attempted to rebuild the package using 
```
dpkg-buildpackage -rfakeroot
```
This is where my main problem came in. When I enter this command, multiple errors pop up and for the life of me I cannot get past this complication. I tried googling this problem but all that came up were bug reports and unanswered questions. I put the results on pastebin as to not make my post bigger than it already is.
[ http://pastebin.com/JnBS85VK]("http://pastebin.com/JnBS85VK")
Again thank you for your time for helping me.

---

### Post by QIII on 2015-12-23
*Moved to **Gaming & Leisure***

The Installation and Upgrades section is for questions about the OS.

Anyway, this section might best capture the attention of those who deal with such things.

---

### Post by tekkah56 on 2015-12-23
Here are two of the errors that came up when I tried rebuilding the package
```
make[1]: *** No rule to make target `distclean'.
```
and
```
dpkg-source: error: can't build with source format '3.0 (quilt)': no  upstream tarball found at ../bluez_4.101.orig.tar.{bz2,gz,lzma,xz}
dpkg-buildpackage: error: dpkg-source -b bluez gave error exit status 255
```

---

### Post by tekkah56 on 2015-12-31
Bump. I really need help connecting my controller. I've solved some issues but I am still stuck at
```
dpkg-buildpackage -rfakeroot
```

---

