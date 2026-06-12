---
title: "/dev/loop0"
date: 2008-06-01
forum: Desktop Environments
---

### Post by gman2004 on 2008-06-01
Here are the results from fdisk and blkid.
If Ubuntu can see my partitions, why it is creating /dev/loop0 and /dev/loop1?

[COLOR="Red"]**[SIZE="4"]sudo fdisk -lu[/SIZE]** [/COLOR]

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22816646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    80292869    40146403+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1dd61dd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   116535509    58267723+   7  HPFS/NTFS
/dev/sdb2       116535510   229440329    56452410   83  Linux
/dev/sdb3       229440330   233360189     1959930   82  Linux swap / Solaris
/dev/sdb4       233360190   390716864    78678337+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b5a8867

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   163413179    81706558+   7  HPFS/NTFS
/dev/sdc2       163413180   327260114    81923467+   7  HPFS/NTFS
/dev/sdc3   *   327260115   490223474    81481680    b  W95 FAT32

Disk /dev/sdd: 2029 MB, 2029518848 bytes
129 heads, 32 sectors/track, 960 cylinders, total 3963904 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32     3963903     1981936    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 128, 32) logical=(960, 31, 32)


**[SIZE="4"][COLOR="Red"]sudo blkid[/COLOR][/SIZE]**

[COLOR="DarkOrange"]/dev/sda1: UUID="291FFF8DB126DFDA" LABEL="SHARED" TYPE="ntfs"[/COLOR] 
/dev/sdb1: UUID="1C04E7FE04E7D8B2" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sdb2: UUID="d84af76b-82cc-4480-b859-49ba02a131e5" TYPE="ext3" 
/dev/sdb3: TYPE="swap" 
/dev/sdc1: UUID="C20C2CCC0C2CBCF3" LABEL="APPLICATIONS" TYPE="ntfs" 
[COLOR="YellowGreen"]/dev/sdb4: LABEL="UBUNTU" UUID="E7CC-D2F9" TYPE="vfat"[/COLOR] 
/dev/sdc2: UUID="5A307E9E2B17B0D8" LABEL="GAMES" TYPE="ntfs" 
/dev/sdc3: LABEL="COMMON" UUID="4599-8ED3" TYPE="vfat" 
/dev/sdd1: SEC_TYPE="msdos" UUID="C2F8-E4F2" TYPE="vfat" 
[COLOR="YellowGreen"]/dev/loop0: LABEL="UBUNTU" UUID="E7CC-D2F9" TYPE="vfat" [/COLOR]
[COLOR="DarkOrange"]/dev/loop1: UUID="291FFF8DB126DFDA" LABEL="SHARED" TYPE="ntfs" [/COLOR]
george@ubuntu:~$

---

### Post by bingoUV on 2008-06-01
Can you post the output of 
```

sudo /sbin/lsmod | grep loop

```

---

### Post by gman2004 on 2008-06-03
It returned:

loop                          18948  4

---

