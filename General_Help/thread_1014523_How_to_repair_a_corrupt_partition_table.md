---
title: "How to repair a corrupt partition table?"
date: 2008-12-17
forum: General Help
---

### Post by miked860 on 2008-12-17
I am told that I have a corrupt partition table.

```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    472     473-   3799341    b  W95 FAT32
/dev/sda2        473   24320   23848  191559060    f  W95 Ext'd (LBA)
/dev/sda3      12387+  24320   11934-  95859823+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5        473+    596     124-    995967   82  Linux swap / Solaris
/dev/sda6        597+  12386   11790-  94703143+  83  Linux

Disk /dev/sdb: 102 cylinders, 173 heads, 57 sectors/track
Units = cylinders of 5048832 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+    101     102-    502885+   b  W95 FAT32
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2e1d2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7598744     3799341    b  W95 FAT32
/dev/sda2         7598745   390716864   191559060    f  W95 Ext'd (LBA)
/dev/sda3       198997218   390716864    95859823+   7  HPFS/NTFS
/dev/sda5         7598871     9590804      995967   82  Linux swap / Solaris
/dev/sda6         9590868   198997154    94703143+  83  Linux

Disk /dev/sdb: 514 MB, 514981888 bytes
173 heads, 57 sectors/track, 102 cylinders, total 1005824 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x211a2b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51     1005821      502885+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.                                 
ubuntu@ubuntu:~$
```

---

### Post by Polygon on 2008-12-18
See if gparted can see the partitons, and then for each one right click each partition (make sure its not mounted, or use a live cd if its the main disk) and select 'check' and it will run the corresponding 'fsck' command (e2fsck, etc) for that partition type, and maybe that will fix it

---

