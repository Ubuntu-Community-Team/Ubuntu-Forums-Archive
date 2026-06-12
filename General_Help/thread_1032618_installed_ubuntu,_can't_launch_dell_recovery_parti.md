---
title: "installed ubuntu, can't launch dell recovery partition"
date: 2009-01-06
forum: General Help
---

### Post by zachbb on 2009-01-06
I have installed Ubuntu 8.10 on my Dell Inspiron 9400 laptop, my Ubuntu and Windows Vista work fine from the GRUB bootloader. However, I need to restore my windows partition, and none of the dell shortcut keys seem to launch the recovery partition.


This is what I've tried:

I have tried CTRL+F11 as well as F8 and I just can't seem to get into the Dell recovery console.

I also tried using GParted (screenshot attached) to set the recovery partition's boot flag, and then using GRUB to boot into it, but I just get a "bootmgr is missing" error.
 
Here is a copy of fdisk -l:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14333       14594     2096128    c  W95 FAT32 (LBA)
/dev/sda2   *           8        1313    10485760    7  HPFS/NTFS
/dev/sda3            1313       12675    91268096    7  HPFS/NTFS
/dev/sda4           12676       14332    13309852+   5  Extended
/dev/sda5           12676       14256    12699351   83  Linux
/dev/sda6           14257       14332      610438+  82  Linux swap / Solaris

Partition table entries are not in disk order


Any ideas?

---

### Post by zachbb on 2009-01-06
I have edited my first post to include fdisk output and a screenshot of gparted, so it's clear how everything works..

---

### Post by adult swim on 2009-01-06
can you restore from windows when you boot it?

---

### Post by zachbb on 2009-01-06
I don't think so - I don't want to do a Windows System Restore, I want to restore the image that DELL put on it's Dell recovery partition. 

Before installing Ubuntu, pressing F8 or CTRL+F11 when the computer was turning on would load the Dell recovery program (which restores the image), but now, after installing Ubuntu, I can't do this.

---

### Post by adult swim on 2009-01-06
i see what you mean now.  you may wish to check out this link.  [http://www.goodells.net/dellrestore/fixes.htm](http://www.goodells.net/dellrestore/fixes.htm)

---

### Post by erflol on 2009-01-06
Have you tried editing the grub menu to include an entry for the dell partition? 

An entry for windows looks something like this:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


It may be possible to edit the root (perhaps to something like (hd0,1)) so that you can boot into that partition.


Cheers
eRflol

---

### Post by ByKeLaO on 2009-01-06
Normally recovery partitions can be accessed from the Windows bootloader. Try selecting the Windows option in the GRUB bootloader, and **then** hold down F8.

---

### Post by CoffeyW on 2009-01-07
You can try selection the vista partition then tapping F8, a boot menu should appear. Select the top option "repair my computer" which should have vista load a recovery console. Then there should be an option at the very bottom of the list for "Dell Factory Image Restore". The restore will probably wipe out ubuntu.

If it doesn't have the option for the "Dell Factory Image Restore" you can try selecting the command prompt and navigating to the recovery partition then running the restore program manually.

---

### Post by frost151n on 2009-01-07
In HP you have something called 'Recovery Manager' (accessible from the Start Menu) which has an option of creating a Recovery DVD.
If you recovery image still exists, windows should be able to find it and create the DVD for you.
Then its just a matter of booting said DVD.

Alternatively call Dell, tell them you screwed up and request them to send you one.

---

### Post by zachbb on 2009-01-07
> **CoffeyW said:**
> You can try selection the vista partition then tapping F8, a boot menu should appear. Select the top option "repair my computer" which should have vista load a recovery console. Then there should be an option at the very bottom of the list for "Dell Factory Image Restore". The restore will probably wipe out ubuntu.

If it doesn't have the option for the "Dell Factory Image Restore" you can try selecting the command prompt and navigating to the recovery partition then running the restore program manually.

Thanks - I pressed F8 during the Windows boot, followed your instructions, and it worked. 

My Ubuntu partition was still there at the end of the proccess and GRUB was intact! :P

Thanks again!

---

