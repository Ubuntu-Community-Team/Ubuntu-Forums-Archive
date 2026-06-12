---
title: "Overlapping partitions on dual-booting Dell..."
date: 2008-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Karpah on 2008-09-06
hiya, not really sure if this is the best place for this post, but I'm getting so confused on all these partitions and how to fix them.

A couple of months ago I purchased a Dell Inspiron 1525 that came pre-loaded with Vista. I wanted Ubuntu on it as well, so I had a friend do some partitioning and I installed Hardy (Desktop version) on it. I still have all the Dell partitions and Vista as well.

Fast forward to now and I wanted to adjust the partitions, to make the Ubuntu one bigger and the Vista one smaller (and also possibly make another for shared data). I tried to use gparted for this and it said I had a hard drive of unallocated space, because of overlapping partitions.

Running fdisk -l gives me the following:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        9111    62629402+   7  HPFS/NTFS
/dev/sda4            9112       14594    44035158+   f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6            9112        9372     2096419+  82  Linux swap / Solaris
/dev/sda7            9373       14266    39311023+  83  Linux

Partition table entries are not in disk order

```

I don't know much what it means, but I can see the overlap between sda1, sda4 and sda5. Doing a quick forum search leads me to testdisk, which gives me following output for testdisk /list:

```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63, sector size=512

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
     Partition			Start        End    Size in sectors
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]
 2 P HPFS - NTFS              8   8  1  1313 114 17   20971520 [beta]
 3 * HPFS - NTFS           1314   0  1  9110 254 63  125258805 [alpha]
 4 E extended LBA          9111   1 62 14593  33 32   88070317
Only one partition must be bootable
Space conflict between the following two partitions
 4 E extended LBA          9111   1 62 14593  33 32   88070317
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]
 5 L Sys=DD               14266 230 45 14593  33 32    5240832
   X extended              9111   1 63  9371 254 63    4192840
 6 L Linux Swap            9111   2  1  9371 254 63    4192839
   X extended              9372   0  1 14265 254 63   78622110
 7 L Linux                 9372   1  1 14265 254 63   78622047

```

alpha: my Vista partition
beta: Dell recovery partition

I'm hesitant to just accept everything testdisk offers me on an analyze because it offers me this:

```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     7 254 63     128457 [DellUtility]
P FAT32 LBA                8   0  1  4185 254 63   67119570 [NO NAME]
P Linux Swap            9111   2  1  9371 254 40    4192816
L Linux                 9372   1  1 14265 254 56   78622040
L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]

```

where I believe [NO NAME] is my former alpha partition (but if I press p to list files, it says the filesystem is damaged), and beta has disappeared entirely! And I don't know what the DellUtility is...

How can I get out of this situation with the least amount of damage? :confused: And is there some Linux tool I can run that will back up the entire hard drive, all the partitions, before I start doing anything?

Hoping anyone can help,
Rebecca

ps. I asked the same friend who did the initial partitioning to have a look at it, and he insisted either I had damaged it, or I had a failing hard drive, so no help there :(

---

