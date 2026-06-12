---
title: "Error while installing TuxRacer"
date: 2005-11-19
forum: Gaming &amp; Leisure
---

### Post by elreteipos on 2005-11-19
Hello,

This is the output of the console when I try to install TuxRacer:```
ubuntu@ubuntu:~$ **cd /home/ubuntu/Desktop/tuxracer-0.61**
ubuntu@ubuntu:~/Desktop/tuxracer-0.61$ **./configure**
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnuoldld
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
ubuntu@ubuntu:~/Desktop/tuxracer-0.61$
```What could be wrong? (I'm using a Live-CD)

---

### Post by RAOF on 2005-11-19
In order to compile stuff, you'll need the 'build-essential' package.  Alternatively, tuxracer is in the repositories, so installing it will be as simple as "sudo apt-get install tuxracer"

---

### Post by elreteipos on 2005-11-19
I can't use my internet connection with Linux, so I can't use the repositories...

---

### Post by RAOF on 2005-11-19
Well, build-essential might be on the livecd, I don't know.  I **do** know that it contains all the stuff you need.

Why can't you use your internet connection in linux?

---

### Post by elreteipos on 2005-11-19
Well, I have [the driver I need]("http://linux-lc100020.sourceforge.net/") but I don't know how to install it. (I have two PC's. On the first PC, I installed Ubuntu and on the second PC, I use the Live CD sometimes.)

---

