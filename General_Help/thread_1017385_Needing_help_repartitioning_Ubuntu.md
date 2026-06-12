---
title: "Needing help repartitioning Ubuntu"
date: 2008-12-21
forum: General Help
---

### Post by magicalman315 on 2008-12-21
I have been dual-booting Ubuntu and Windows on my Dell laptop for quite some time now, but I only gave Ubuntu a 60 gig partition, which is getting tight for me. I really like Ubuntu and haven't booted into windows since my Linux install, so I want to lose windows entirely. Is there a way I can repartition Linux to have the full 320 gigs without having to remove and reinstall Linux completely? 


Many thanks,


John

---

### Post by taurus on 2008-12-21
What does your harddrive layout look?  From Ubuntu, open a terminal and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by tad1073 on 2008-12-21
get gparted, open it, delete windows partition, move ubuntu to the right and grow ubuntu to use the entire disk.

It will take a couple of hours for the process t complete so I suggest finding something to do in the mean time.

---

### Post by magicalman315 on 2008-12-21
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317       24417   185546875    7  HPFS/NTFS
/dev/sda4           24418       38914   116440273    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           24418       38005   109145578+  83  Linux
/dev/sda7           38006       38586     4666851   82  Linux swap / Solaris

Partition table entries are not in disk order


Also to tad1073: I ran gparted and all it sees is one large unallocated drive. I am so lost...

---

### Post by Alvinius on 2008-12-21
Using Gparted or not you need to do a backup, I suggest you backup and start from scratch... a clean OS install

---

### Post by magicalman315 on 2009-01-08
So I have tried running gparted from the 8.04 live cd, and it too sees one large unallocated drive. I am thinking a total wipe and reinstall for ubuntu only, and definitely not windows, might be in order.

---

