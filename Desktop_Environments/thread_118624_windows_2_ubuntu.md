---
title: "windows 2 ubuntu"
date: 2006-01-17
forum: Desktop Environments
---

### Post by wolf4475 on 2006-01-17
i have windows xp and i want to put ubuntu on . & i have lots of games & programs & music. will my games & programs & music stay or will i have to seet them back up:confused:

---

### Post by newuser111 on 2006-01-17
not if you resize the partition and install grub

---

### Post by bikeman on 2006-01-17
Hi, and welcome to Ubuntu.  There are a lot of good tips in these forums, the official guide, and the unofficial guide.

You can add Ubuntu to a PC already running Windows fairly easily.  The easiest way is if you have a separate hard drive - leave Windows on one and put Ubuntu on the other.  However, if you only have one drive, you can still do it.  First, run a disk cleanup and delete everything that you don't need, such as tmp files, Internet cache, etc.  Once that is done, run a full disk defrag.  Once that is done, you need to re-partition your disk to make your Windows partition smaller and make room for Ubuntu.  I used Partition Magic since I had it and was familiar with it.  There is also an option to do this in the Ubuntu installation, but never having used it, I cannot say anything about it.

When you run the installation, just be sure to **NOT** select the option to take over the whole drive - that will erase Windows.  GRUB (the GRand Unified Bootloader) is the bootloader used by Ubuntu.  It should automatically see your Windows installation and add it to the boot menu.  Have fun!

---

### Post by dragonfyre13 on 2006-01-17
Question
   Go to first new post windows 2 ubuntu 
wolf4475 
   1 Minute Ago 
 by bikeman Go to last post 
  2  3  Desktop Support
   
   Question
   Go to first new post windows 2 ubuntu 
wolf4475 
   2 Minutes Ago 
 by tkjacobsen Go to last post 
  1  2  Installation and Upgrade Help

Please do not double post in multiple sub-forums anymore.

---

