---
title: "Grub Error 22 no such partition"
date: 2009-04-28
forum: General Help
---

### Post by rincewind456 on 2009-04-28
I can't get to my WinXP partition. Get an Error 22 no such partition.

In intrepid I had no problems booting to Windows but since installing Jaunty I can't get into my Windows XP partition, this is the grub menu.lst entry:

title		Microsoft Windows XP Professional
rootnoverify	(hd2,1)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

I have tried the following:

1. Using a Windows installer disc I have reset the MBR and booted fine into windows, just to prove that the windows partition is still there and working.

2. I've gone through every permutation of disc/partition numbers from 0,0 to 3,4 my discs are :
lrwxrwxrwx 1 root root 10 2009-04-25 14:25 99cf22c2-e628-4638-bc8c-0c25d9c33f34 -> ../../sda1	-->	/music

lrwxrwxrwx 1 root root 10 2009-04-25 14:25 140ba0c2-506d-4244-b3cb-3a9ce2af273e -> ../../sdb1	-->	/(root partition)

lrwxrwxrwx 1 root root 10 2009-04-25 14:25 8553d9f1-5e82-44b2-b364-557dbead76b5 -> ../../sdc1	-->	/boot
lrwxrwxrwx 1 root root 10 2009-04-25 14:25 40680CA5680C9BB2 -> ../../sdc2			-->	Windows XP
lrwxrwxrwx 1 root root 10 2009-04-25 14:25 3abc9d68-9255-44a7-a098-1077b7d99f6f -> ../../sdc3	-->	/extra
lrwxrwxrwx 1 root root 10 2009-04-25 14:25 2b2c8097-07d9-425f-b9ea-69e22cec32e2 -> ../../sdc4	-->	/swap

lrwxrwxrwx 1 root root 10 2009-04-25 14:25 821a14e0-90b3-4996-bb7a-e71f813ba36b -> ../../sdd1	-->	/home/user/backup

3. Re-installed GRUB and it boots fine into Intrepid.

Output from fdisk -l is:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022bd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008dcda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb0afb0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          45      361431   83  Linux
/dev/sdc2              46        9885    79039768+   7  HPFS/NTFS
/dev/sdc3           10012       30515   164698380   83  Linux
/dev/sdc4   *        9886       10011     1012063+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b7a6e9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   83  Linux
/dev/sdd4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

I've searched here and can't find the answer, can anybody offer any advice.

---

