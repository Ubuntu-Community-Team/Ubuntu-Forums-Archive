---
title: "Dual Boot/ Drive Problems"
date: 2009-02-19
forum: General Help
---

### Post by liks2kikpupes on 2009-02-19
Ok, so I Dual Boot into Windows Vista as well as Intrepid, I also have to drives one of them only containing my music and other media files, in Vista its listed as 'D' and in Linux its listed as "DATA." Its not so much a problem with my Linux, but whenever I boot into Vixta and try to access my drive with my music and stuff on it will wont read it, and it will tell me that its curopeted. However, it works fine on my Linux so i was wondering if someone could tell me what I should do, or direct me somewhere else for correcting this problem?

---

### Post by darco on 2009-02-19
How was the drive formatted, NTFS or EXT3?

darco

---

### Post by liks2kikpupes on 2009-02-19
ntfs, also the way my linux is setup, it is mounted when i log on, could this have something to do with it?

---

### Post by darco on 2009-02-20
I just added a 2nd SATA drive and it automounts in Linux. In Win7 it appears fine as well.
Show the output for ```
sudo fdisk -l
```

darco

---

### Post by liks2kikpupes on 2009-02-20
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31b60ab5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       10367    73028608    7  HPFS/NTFS
/dev/sda3           10367       19458    73019392    7  HPFS/NTFS

Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders
Units = cylinders of 240 * 512 = 122880 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       16384     1965952+   6  FAT16

---

### Post by darco on 2009-02-20
I dont understand how you setup your partitions. I see two drives but no linux partitions. I did notice the storage is FAT16????..heres my output w/two drives. ...SDA is the Linux/Vista drive and SDB is my storage drive:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe868f6fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34482   276976633+   7  HPFS/NTFS
/dev/sda2           35919       60801   199872697+  83  Linux
/dev/sda3           34483       34515      265072+  82  Linux swap / Solaris
/dev/sda4           34516       35918    11269597+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017ea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           34536       60801   210981645    7  HPFS/NTFS
/dev/sdb2           21482       34535   104856255    7  HPFS/NTFS
/dev/sdb3               1       21481   172546101    7  HPFS/NTFS

darco

---

### Post by liks2kikpupes on 2009-02-20
all right, well ill just have to continue to look into it. i appreciate your help

---

