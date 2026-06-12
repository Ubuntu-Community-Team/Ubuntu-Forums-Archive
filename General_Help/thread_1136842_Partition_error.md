---
title: "Partition error"
date: 2009-04-25
forum: General Help
---

### Post by letmekilluplz on 2009-04-25
I have a 250GB external hard drive and partitiond it for 30GB to install Ubuntu before I installed it for good just so I can scope it out for a few days

The problem is I deleted the partition but it still shows up as my total capicity is 203GB (It had 232GB before) When I open g parted it shows one partition but im missing 30 GB of memory please help!

---

### Post by kpkeerthi on 2009-04-25
With your external drive plugged in, can you post the output of
```
sudo fdisk -l
```

Also a screenshot of gparted might help.

---

### Post by Ericyzfr1 on 2009-04-25
If you deleted the partition it just become unallocated space on your HD. You need  then to resize your original partition or create a new one.

---

### Post by letmekilluplz on 2009-04-25
> **Ericyzfr1 said:**
> If you deleted the partition it just become unallocated space on your HD. You need  then to resize your original partition or create a new one.I did resize

Ill post fdisk soon

---

### Post by letmekilluplz on 2009-04-25
Fdisk -l output

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00b00485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73168042+   6  FAT16
/dev/sda3           10384       19457    72886905   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea9be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---

### Post by letmekilluplz on 2009-04-26
bump

---

### Post by sgosnell on 2009-04-26
Well, fdisk says it's a 250GB drive.  Run gparted and make sure you have what you think you have.  I'm betting on unallocated space, but it's possible the other partition is still there.  If you can post a screenshot of gparted it would help us identify the problem.

---

### Post by letmekilluplz on 2009-04-26
it says in gparted its one partition with 232GB so thats right(its what it said when I got it) but if you select properties on the drive it shows 203GB

---

### Post by sgosnell on 2009-04-26
There is also about a 30GB difference in the amount of used space between the two.  

FWIW, Google shows a number of problems with Seagate FreeAgent drives under Linux.  Apparently Seagate has no interest in supporting Linux.

---

### Post by letmekilluplz on 2009-04-26
> **sgosnell said:**
> There is also about a 30GB difference in the amount of used space between the two.  

FWIW, Google shows a number of problems with Seagate FreeAgent drives under Linux.  Apparently Seagate has no interest in supporting Linux.

ok well i suppose theres nothing that can be done but im curious what does FWIW mean

---

### Post by meierfra. on 2009-04-26
Maybe your partition is 232GiB but the filesystem is 203GiB.

Try this

```
sudo umount /dev/sdb1
sudo ntfsresize /dev/sdb1
```

This will expand the filesystem to the full size of the partition.

---

### Post by sgosnell on 2009-04-27
FWIW = For What It's Worth.

---

