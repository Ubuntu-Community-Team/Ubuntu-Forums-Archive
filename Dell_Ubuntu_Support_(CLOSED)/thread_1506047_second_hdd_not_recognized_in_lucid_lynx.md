---
title: "second hdd not recognized in lucid lynx"
date: 2010-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kRaYvYn on 2010-06-09
hello, i am new to linux all around, i was an AVID windows user since 3.2, long story short i have obviously come to the superior OS. However seeing my second HDD is a problem, i have partitioned my second hdd, but i cannot seem to mount it

when i used fdisk this is my results

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e877a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38163   306537472   83  Linux
/dev/sda2           38163       38914     6031361    5  Extended
/dev/sda5           38163       38914     6031360   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005a97

   Device Boot      Start         End      Blocks   Id  System


this is problematic for me

my backup hdd is labeled sdb, but how do i mount it so i can utilize it?

---

### Post by Jest3r on 2010-06-10
Looks like the 2nd disk hasn't been formatted,

Can you post the full output of the command below.

```
sudo fdisk -l /dev/sdb
```



You may Disk Utility software useful (found here: System > Administration > Disk Utility)

---

### Post by kRaYvYn on 2010-06-10
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005a97

   Device Boot      Start         End      Blocks   Id  System


here ya go

---

### Post by kRaYvYn on 2010-06-10
ok odd thing just happened, ran my disk utility, formatted second hdd to apple partition, now i can't see either of my hdd's

---

### Post by kRaYvYn on 2010-06-12
?

---

