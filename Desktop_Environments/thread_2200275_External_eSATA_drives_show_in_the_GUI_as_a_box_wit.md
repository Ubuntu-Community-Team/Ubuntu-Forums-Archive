---
title: "External eSATA drives show in the GUI as a box with question mark"
date: 2014-01-18
forum: Desktop Environments
---

### Post by mike.lussier on 2014-01-18
Good morning all, 

This problem has been bothering me for several weeks. 
I have 2 ESATA cases that connect to a ESATA card in my computer. All 8 drives are seen and I can move files back and forth. my NFS works great. 

but, 
in the gui all of the ESATA drives look like squares with question marks in them and not actual hard drives.  THe question is how do I fix this ?

Here is what I see in /etc/fstab and fdisk -l 

Any thoughts ? 

Thank you ..


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=405b3c17-c5ac-45cb-a87a-6dcbf48dfd11 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5b483989-70fc-43c5-a995-cb8361d66219 none            swap    sw              0       0
/dev/disk/by-uuid/68F4C6BCF4C68C2E /media/drive_0x1 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_0x1,x-gvfs-icon=Drive_0x1,x-gvfs-symbolic-icon=Drive_0x1 0 0
/dev/disk/by-uuid/DA58DE2A58DE04E3 /media/drive_0x2 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_0x2,x-gvfs-icon=Drive_0x2,x-gvfs-symbolic-icon=Drive_0x2 0 0
/dev/disk/by-uuid/9E30F26130F24037 /media/drive_0x3 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_0x3,x-gvfs-icon=Drive_0x3,x-gvfs-symbolic-icon=Drive_0x3 0 0
/dev/disk/by-uuid/244B5020222C1266 /media/drive_0x4 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_0x4,x-gvfs-icon=Drive_0x4,x-gvfs-symbolic-icon=Drive_0x4 0 0
/dev/disk/by-uuid/0822DB5022DB417C /media/drive_1x1 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_1x1,x-gvfs-icon=Drive_1x1,x-gvfs-symbolic-icon=Drive_1x1 0 0
/dev/disk/by-uuid/BE80AE4280AE014F /media/drive_1x2 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_1x2,x-gvfs-icon=Drive_1x2,x-gvfs-symbolic-icon=Drive_1x2 0 0
/dev/disk/by-uuid/467CEF3A7CEF2401 /media/drive_1x3 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_1x3,x-gvfs-icon=Drive_1x3,x-gvfs-symbolic-icon=Drive_1x3 0 0
/dev/disk/by-uuid/825A2B955A2B84CF /media/drive_1x4 auto nosuid,nodev,nofail,x-gvfs-show,x-udisks-auth,x-gvfs-name=Drive_1x4,x-gvfs-icon=Drive_1x4,x-gvfs-symbolic-icon=Drive_1x4 0 0

/media/drive_1x3/Music /exports/Music none bind
/media/drive_1x3/Movies  /exports/Movies none bind
/media/drive_1x3/TV_Shows /exports/TV_Shows none bind


========
root@mediaserver-Inspiron-620:/home/media-server# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea6f47b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    31141887    15529984    7  HPFS/NTFS/exFAT
/dev/sda3        31141888   535994367   252426240    7  HPFS/NTFS/exFAT
/dev/sda4       535996414   976771071   220387329    5  Extended
/dev/sda5       535996416   960030719   212017152   83  Linux
/dev/sda6       960032768   976771071     8369152   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea6f479a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976771071   488384512    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x290a6c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb720bbd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x09404c7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x09404c7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcaac071c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcaac071e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdi'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcaac0702

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b407f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1            2048  3907029167  1953513560    7  HPFS/NTFS/exFAT

---

### Post by mike.lussier on 2014-01-18
I found my fix 


/dev/disk/by-uuid/68F4C6BCF4C68C2E /media/drive_0x1 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/DA58DE2A58DE04E3 /media/drive_0x2 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/9E30F26130F24037 /media/drive_0x3 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/244B5020222C1266 /media/drive_0x4 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/0822DB5022DB417C /media/drive_1x1 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/BE80AE4280AE014F /media/drive_1x2 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/467CEF3A7CEF2401 /media/drive_1x3 auto nosuid,nodev,nofail,x-gvfs-show  0 0
/dev/disk/by-uuid/825A2B955A2B84CF /media/drive_1x4 auto nosuid,nodev,nofail,x-gvfs-show  0 0

---

