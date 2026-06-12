---
title: "Can't see Vista partition in Places"
date: 2009-03-26
forum: General Help
---

### Post by psychoadonis on 2009-03-26
This is what I get when I type fdisk:

psychoadonis@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1280       38914   302289240    7  HPFS/NTFS
psychoadonis@ubuntu:~$

---

### Post by psychoadonis on 2009-04-05
Come on guys, I could use some help here.

And here: [http://ubuntuforums.org/showthread.php?p=6962436](http://ubuntuforums.org/showthread.php?p=6962436)

---

