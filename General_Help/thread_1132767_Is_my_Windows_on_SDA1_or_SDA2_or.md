---
title: "Is my Windows on SDA1 or SDA2 or?"
date: 2009-04-22
forum: General Help
---

### Post by GapToN on 2009-04-22
Hi guys, I have had experience with Ubuntu but never configured my partitions much. I currently have Dual Boot vista + ubuntu installed, and Im following a guide which will need me to point to my Vista partition.

My question is, how do I find out where is my Windows partition?

Heres my fdisk -l

```


************* first physical HD, both Vista and Ubuntu should be on here ******************
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebcbebcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30720000    7  HPFS/NTFS
/dev/sda2            3825        7650    30720000    7  HPFS/NTFS
/dev/sda3            7651        9729    16699567+   5  Extended
/dev/sda5            7651        9636    15952513+  83  Linux
/dev/sda6            9637        9729      746991   82  Linux swap / Solaris

**************** this is my second physical SATA hd **************
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000fe1e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18241   146518816+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           18241       30401    97677153+   f  W95 Ext'd (LBA)
/dev/sdb5           18241       30401    97677122    7  HPFS/NTFS


******* this is my external hd ********************************
Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    7  HPFS/NTFS

```

Now while I'm sure it is either sda1 or sda2, I'm not sure which
sda1 has the boot * on it, but since I have dual boot (installing ubuntu AFTER vista), the actual first "thing" to be loaded is the grub loader.

And I'm also wondering, wheres sda4 gone in my first HD?

---

### Post by unutbu on 2009-04-22
Install the os-prober package. (about 150 KiB in size).
In a terminal, run
```

sudo os-prober
```
> 
wheres sda4 gone in my first HD?
There is a funny rule which says sda1,sda2,sda3,sda4 can be primary or extended partitions, but logical partitions must have names like sda5,sda6,etc. 

You have 2 primary partitions, sda1 and sda2.
You have 1 extended partition, sda3.
To satisfy the rules above, your logical partitions were named sda5 and sda6.

---

### Post by GapToN on 2009-04-22
Thanks for the quick reply, and the extra information :D

---

