---
title: "Error 21"
date: 2009-05-11
forum: General Help
---

### Post by bunbut on 2009-05-11
Hi,

Very newbie here, please help.  This is what I got right now when boot up

GRUB Loading stage 1.5

GRUB loading, please wait...
Error 21

My system was running XP on SATA drive.  I plug in a SCSI drive and install Ubuntu 9.04 on it.


fdisk -lu:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8a16212

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 36.7 GB, 36703934464 bytes
255 heads, 63 sectors/track, 4462 cylinders, total 71687372 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99d69c5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    48516299    24258118+  83  Linux
/dev/sdb2        48516300    71682029    11582865    5  Extended
/dev/sdb5        48516363    71682029    11582833+  82  Linux swap / Solaris

I can mount /dev/sdb1 and access Linux

Last few lines of /boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1


Thank you for helping.

---

### Post by baseface on 2009-05-11
use the search function.

[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

also use google.

[http://www.google.com/#hl=en&q=grub+error+21&fp=ry0_Tod3DXA](http://www.google.com/#hl=en&q=grub+error+21&fp=ry0_Tod3DXA)

---

