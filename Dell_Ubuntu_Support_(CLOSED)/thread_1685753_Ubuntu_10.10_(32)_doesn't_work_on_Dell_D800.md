---
title: "Ubuntu 10.10 (32) doesn't work on Dell D800"
date: 2011-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vorob on 2011-02-11
So i downloaded 10.10 ubuntu and thats what i have:
[http://dl.dropbox.com/u/5020311/DSC00732.JPG](http://dl.dropbox.com/u/5020311/DSC00732.JPG)

Config:
[http://dl.dropbox.com/u/5020311/delld800.jpg](http://dl.dropbox.com/u/5020311/delld800.jpg)

---

### Post by gbrainin on 2011-02-11
This is largely a guess, since I don't have a lot of context, but being dropped into the "busybox" prompt is what happened on my Inspiron 530 a few versions ago.

So, it wouldn't hurt to try the solution that worked on my 530.  Get into the BIOS setup and see if there is a setting for SATA mode with options for IDE or RAID.  Set it to RAID and see if Ubuntu works correctly.  If it doesn't work, set it back to where it was.

Note that if you're trying to dual-boot with Windows, Windows may not work in RAID mode.  In that case, you'll have to leave the BIOS in IDE mode and add the all_generic_ide boot flag to your Ubuntu setup.

---

### Post by vorob on 2011-02-11
I see, but its an ancient laptop with IDE hdd, so there are not sata :) Now i'm burning another cd to see if its disk error, not laptop or ubuntu

---

### Post by gbrainin on 2011-02-11
Well, I was just guessing to begin with.  I would suggest trying a bootable USB stick instead of a CD, but I'm not sure a laptop that old can boot off of a USB device.

---

### Post by wilee-nilee on 2011-02-11
Try the alternate cd for installing, you may be a bit low on memory.

---

### Post by vorob on 2011-02-13
Tried LTS version and GFX really corrupted 

[http://dl.dropbox.com/u/5020311/DSC00768.JPG](http://dl.dropbox.com/u/5020311/DSC00768.JPG)
[http://dl.dropbox.com/u/5020311/DSC00767.JPG](http://dl.dropbox.com/u/5020311/DSC00767.JPG)
[http://dl.dropbox.com/u/5020311/DSC00766.JPG](http://dl.dropbox.com/u/5020311/DSC00766.JPG)

---

