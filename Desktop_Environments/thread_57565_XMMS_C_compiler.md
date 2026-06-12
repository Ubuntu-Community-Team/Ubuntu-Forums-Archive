---
title: "XMMS C compiler"
date: 2005-08-17
forum: Desktop Environments
---

### Post by FrozenDice on 2005-08-17
Unfortunatly Ubuntu doesn't come with a media player that supports streaming audio/video so I thought I would go and grab the good old trusty XMMS.  I got the downloading, and unpacking alright but when I configure it says 


./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH  <--- Thats the offender!
See `config.log' for more details.

---

### Post by jasmuz on 2005-08-17
Do you have the build-essential package installed? In order to compile anything you must have them.

---

### Post by FrozenDice on 2005-08-17
I havn't installed anything so far besides the basic OS.  I'm just confused by what you mean by "bare-essentials" is this the name of a program or what?   ](*,)   Wish I knew more.  Thanks for helping.

---

