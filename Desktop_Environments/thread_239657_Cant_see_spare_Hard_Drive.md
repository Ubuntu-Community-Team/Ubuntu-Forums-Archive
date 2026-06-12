---
title: "Cant see spare Hard Drive"
date: 2006-08-19
forum: Desktop Environments
---

### Post by cornish on 2006-08-19
Hi

I have three Hard Drives installed on my PC, when I was using the live version I could click Places from Gnome menu and see them in the list but after installing Ubuntu they are not there.

When I click on computer I can see them in there but I cant access them I get the following error message

error: device /dev/hdb1 is not removable

error: could not execute pmount

FYI:

fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14026   112663813+  83  Linux
/dev/hda2           14027       14593     4554427+   5  Extended
/dev/hda5           14027       14593     4554396   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4862    39053983+  83  Linux

Disk /dev/hdc: 13.5 GB, 13578485760 bytes
255 heads, 63 sectors/track, 1650 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1650    13253593+   c  W95 FAT32 (LBA)

Can any one tell me how I can gain access to them again and have them appear on the Places menu

---

### Post by lagagnon on 2006-08-19
Check that in your /etc/fstab file you have the following line:

/dev/hdb1       /media/hdb1     ext3       defaults        0       2


It should then automount on boot and you will get an icon on the desktop.

---

