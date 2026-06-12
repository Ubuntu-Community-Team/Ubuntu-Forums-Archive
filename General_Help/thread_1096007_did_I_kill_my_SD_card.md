---
title: "did I kill my SD card?"
date: 2009-03-14
forum: General Help
---

### Post by maestrobwh1 on 2009-03-14
I have an 8-GB SD card (A-data).

The reader popped out while transferring data and the card would no longer read. It shows as only **512K**.

Under fdisk -l

Disk /dev/sdb: 0 MB, 524288 bytes
1 heads, 1 sectors/track, 1024 cylinders, total 1024 sectors
Units = cylinders of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

And when I try to do 

sudo fdisk -b 512 -C 997 -H 255 -S 63 /dev/sdb (specs are from an identical card I own)  

and create a partition starting at 1 and ending at 997, and then do 

fdisk -l

I get 

Disk /dev/sdb: **0 MB,** 524288 bytes
255 heads, 63 sectors/track, **0 cylinders**
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         997     8008371   83  Linux

[B]
Is this card "dead?"[/B]

---

