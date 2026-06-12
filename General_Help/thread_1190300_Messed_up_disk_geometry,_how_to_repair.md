---
title: "Messed up disk geometry, how to repair?"
date: 2009-06-17
forum: General Help
---

### Post by helwitch on 2009-06-17
I have a 16gb microsdhc card which I use in my g1 phone. In the course of trying to update the firmware of my phone, the card got messed up. It had previously been partitioned with a 14GB fat32 partition, and a 2gb ext3 partition. After the attempted update, the card reads as if it is a 14GB card. I have tried it in kubuntu, xubuntu, and windows vista, all with the same results.
 I have another of these cards which is not messed up, and when I fdisk -l both cards, I get very different results. It seems clear the problem with my card is the disk geometry, but I have no idea how to reset that. I tried using fdisk and cfdisk to create a partition after manually setting the heads, sectors, and cylinders, but it didn't work. cfdisk said the partition was larger than the disk, and fdisk just...didn't actually do anything. How do I fix this? I'd prefer a linux solution, but I can boot windows if necessary.

fdisk -l on the good card returns ```
Disk /dev/sdb: 16.0 GB, 16070475776 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1d1d
```
While fdisk -l on the messed up card returns ```
Disk /dev/sdb: 14.0 GB, 14044626944 bytes
64 heads, 32 sectors/track, 13394 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x56ee5dbf
```

---

