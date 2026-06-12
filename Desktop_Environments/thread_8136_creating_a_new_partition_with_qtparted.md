---
title: "creating a new partition with qtparted"
date: 2004-12-14
forum: Desktop Environments
---

### Post by darkwithstars on 2004-12-14
would creating a new partition with qtparted and then formatting to ntfs. installing winxp and then using a linux boot disk allow me to successfully dual boot win xp and ubuntu?

how would i go about creating the partition if so?

---

### Post by az on 2004-12-14
You need to unmount you disk to partition it.  If you have more than one disk, you should boot an os on another disk than the on eyou want to partition.  If you only have one disk, boot the Ubuntu installer and use it to partition.  It runs from a ramdisk...

I have never used windows Xp, so maybe someone else can tell you if it is possible to put Windows on a partition which is after linux or if it need to come first.

---

### Post by jdong on 2004-12-14
Tips: The **knoppix, kanotix** livecd's have QTParted on them with FULL capability -- including safe NTFS resizing.


Qtparted is as easy to use as partition magic... It's a snap.

---

### Post by Rui Pais on 2004-12-14
Mandrake Moves (live CD) has a GUI partition tool very good too, check the smaller iso i gess  ;-) 

I think if you want that combination you should start with XP and then the Linuxs (as many as you want!) If you do the other way, Win probabilly will destroy your grub (the boot  software) and cleans the MBR... so you will ended with a XP and a non bootable linux (easy to fix but not trivial)

---

### Post by jdong on 2004-12-14
The smallest is gonna be **SystemRescueCD**, but I don't like the clunky embedded qt runtime!

---

