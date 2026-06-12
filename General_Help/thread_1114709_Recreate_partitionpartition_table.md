---
title: "Recreate partition/partition table?"
date: 2009-04-03
forum: General Help
---

### Post by Nixie Pixel on 2009-04-03
Hi, I have been dual-booting Ubuntu and Vista on a machine with two hard drives.  One is an SSD (OCZ Vertex 60GB), where I installed Vista (Ultimate 64), and the other is a Barracuda 7200.12 500GB (partitioned with 1 100GB NTFS, 3 Linux partitions).  Since I am playing with brand new SSD technology, I got burned - the Vista drive spontaneously lost its partition.

I was able to recreate the boot loader by running grub's setup utility, but it can't boot to Windows since the partition is gone.  Is there a way to recreate the partition without losing my data, or is it gone forever?

Thanks!

---

### Post by lindsay7 on 2009-04-03
type    sudo fdisk -l     (the letter l not number 1) in the terminal and post it. This will show what your drives look like.

---

### Post by Nixie Pixel on 2009-04-03
```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1eb719e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa453fc98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12749   102400000    7  HPFS/NTFS
/dev/sdb2           12750       60801   385977690    5  Extended
/dev/sdb5           12750       13235     3903763+  82  Linux swap / Solaris
/dev/sdb6           13236       15667    19535008+  83  Linux
/dev/sdb7           15668       60801   362538823+  83  Linux
```
That first disk (/dev/sda) used to be full of a Windows Vista 64 partition.

---

### Post by lindsay7 on 2009-04-03
Looks like it is gone for good to me. If there was any data there, once you partition it and format it would be gone anyway. Maybe someone has a solution for you. I can not think of one.

Sorry that happened to you, hope you find an answer.

---

