---
title: "Parition Table Recovery"
date: 2008-08-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DimensionUserInTheUK on 2008-08-28
Hello and thank you for taking in an interest in my post.  I have a Dell Dimension 3100.  The partitions on the one and only disk have seemingly disappeared and i suspect the partition table has been overwritten or corrupted. The system will not boot.  Therefore can any kind person provide me with a output of a linux fdisk command on a factory set 80gb hard disk with only Windows XP installed, i.e.

fdisk -l /dev/sda .


I will then be able to recreate the partitions with a live linux CD.

Many thanks in advance, your assistance will really help me so much.

---

### Post by sandysandy on 2008-08-28
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by paddy1978 on 2008-08-28
I managed to wipe a parition table a few years ago, but managed to recover it with this: [http://www.stud.uni-hannover.de/user/76201/gpart/]("http://www.stud.uni-hannover.de/user/76201/gpart/")

Good luck!

---

### Post by DimensionUserInTheUK on 2008-08-29
Hello again and thank you so much to Sandy and Paddy and the author(s) of Testdisk.

I only needed Testdisk which recovered my partition table and now I have my dual boot system back :-) 

Here are the links I used...

Get TestDisk
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

TestDisk WIKI
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Recover GRUB
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by nolan- on 2008-09-05
Thankyou thankyou thankyou !

Almost lost 750gb of stuff there, admittedly a lot of it is junk but 750gb is a lot, junk or not :)

Sterling stuff thanks for the links DimensionUserInTheUK :guitar:


Nol

---

