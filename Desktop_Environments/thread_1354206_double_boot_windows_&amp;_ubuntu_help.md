---
title: "double boot windows &amp; ubuntu help"
date: 2009-12-13
forum: Desktop Environments
---

### Post by phillychease on 2009-12-13
right now i am running ubuntu 9.1. no double boot. ubuntu is my only OS.
is there a way i can use gparted to create a separate partition for windows.
if i can, how do i install it from the windows setup?

oh i dont want to use a virtual box too.

---

### Post by marin123 on 2009-12-13
do you have free space on your hard drive? if yes, then you can make a new partition with win installer and install windows...
unless you must use partition editor for this...

---

### Post by oldfred on 2009-12-13
This site has several examples of dual boot installs. Plan on reinstalling grub after the windows install as windows will put its boot loader into the MBR. gparted will work just fine for partition changing. Just make sure that you create a primary partition for windows or it will not work.

APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

---

