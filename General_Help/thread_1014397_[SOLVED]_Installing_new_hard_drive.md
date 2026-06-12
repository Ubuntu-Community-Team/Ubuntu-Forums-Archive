---
title: "[SOLVED] Installing new hard drive"
date: 2008-12-17
forum: General Help
---

### Post by fedex1993 on 2008-12-17
Okay got a new 160gb sata drive problem is i want to mount it too /media/mymedia and have it auto mount problem is i want to be able to backup my movies and music but i want to be able to read it in windows and ubuntu is this possible?

---

### Post by taurus on 2008-12-17
Is there a partition (something like /dev/sdb1) and a filesystem on that new harddrive?  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by fedex1993 on 2008-12-17
havnt checked yet i need to install the hard drive first :D

---

### Post by Snow986 on 2008-12-17
My windows can read my ext3 linux partition, I would think it should not be a problem reading it in both.

---

### Post by fedex1993 on 2008-12-17
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebbfebbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS
/dev/sda2           30402       60801   244188000    5  Extended
/dev/sda5           30402       32891    20000893+  83  Linux
/dev/sda6           32892       33015      995998+  82  Linux swap / Solaris
/dev/sda7           33016       60801   223191013+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

tarus there we go.

---

