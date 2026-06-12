---
title: "Won't install from Live CD !"
date: 2006-07-13
forum: Desktop Environments
---

### Post by ozmaXTor on 2006-07-13
hi all,

i just solved the X700 problem and now i can get into the desktop from Live CD. however when i click on the "install" icon on the desktop, it won't install the system on my hard drive!

what i do is click on the icon, then a series of windows pop up for installation information. at the stage where u choose where to install the system, i choose the ext3 partition which i formatted under windows using partitionMagic8.0, i also partitioned a swap space for 400MB. the problem is, when everything seems to be fine, the installation process begins. first it just stuck at 0%, after being stuck for like 2 mins, it starts to check the file system then the program window just simply disappear! nothing happens, i can still run programs from Live CD as if i didn't run the install !

a lil help here pls..... did i do anything wrong??????

im using 6.0.6 final release.

thx for helping!!

---

### Post by taurus on 2006-07-13
Maybe you should try using the alternate CD to install Dapper on your system then!

---

### Post by ozmaXTor on 2006-07-13
well i ordered like, 8 ubuntu for PCs n they r all brand new, shipped in yesterday. is there any chance that it is the CD's problem??? anyway i'll try now, cheers!

---

### Post by taurus on 2006-07-13
Even though you formatted your harddrive to ext3 and swap under PM8 for Linux, I recommand you have Ubuntu format those partitions again.  On the other hand, the video card could be a problem so download the alternate CD and see if you can install Dapper from it.

---

### Post by ozmaXTor on 2006-07-13
er.... thx taurus, u just reminded me another problem. the program Ubuntu uses to format the partitions does not work for me in the installation process! i know it's weird but it just simeply tells me "one or more of your tasks were not completed" then nothing more. that's why i used PM8 under windows....

---

### Post by taurus on 2006-07-13
I am not sure whether it's a good idea to use PM8 to format partitions that you plan to install Ubuntu on!!!  Therefore, I recommand you boot into Windows, convert all those partitions that you plan to put Ubuntu on as a one big partition with fat32 format.  Then, boot up the desktop CD and tell the program to use that large partition and convert it into at least two partitions, / & swap.  Personally, I would go for at least three (/, /boot, & swap) or even four (/, /boot, /home, & swap).

---

