---
title: "Dell1525n - xp dual boot - all partitions used"
date: 2008-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pbarne on 2008-07-09
Hi All,

First post on here - so I hope this is a reasonable question.

I've bought a Dell Inspiron 1525 Ubuntu laptop and want to
dual Boot with XP.

I've been following a guide at apcmag on how to install xp
after linux. I've used gparted to reduce the main partition
to create room and have created win xp sp3 boot disk that
recognises the SATA drive.

I have now got stuck in the windows xp install
as all the four allowed partitions of the disk are used.

The message is:

[FONT="Fixedsys"]"Setup cannot create a new partition in the space you selected because the maximum number of partitions already exists on the disk."[/FONT]

My disk looks like:

[FONT="Fixedsys"]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13         665     5245222+   b  W95 FAT32
/dev/sda3   *         666        2689    16257780   83  Linux
/dev/sda4           14022       14593     4594590    5  Extended
/dev/sda5           14022       14593     4594558+  82  Linux swap / Solaris
[/FONT]

What are my options?

Thanks,

Paul

---

### Post by stats on 2008-07-09
3 primary partitions with dell utility, xp and /boot(around 128 mb will do)
extended partition having swap, /, /home and others
install xp first
make /boot bootable during ubuntu install

---

