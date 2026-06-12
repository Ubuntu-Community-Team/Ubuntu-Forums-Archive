---
title: "Permissions and priviledges..."
date: 2010-06-05
forum: Desktop Environments
---

### Post by Moozillaaa on 2010-06-05
I want to add UNIVERSAL root privileges/permissions to my account, on every computer in my house.

I just created a partition on my primary hard disk, then restarted X, and could not add a folder to my new partition. :x 

As well, I have so many shared files, folders, drives on my network, but I still run into read/write permissions, that I have to go into another room to change the permissions of the file, and HOPE it refreshes properly.

With respect to EVERYTHING inside my network, I want NO questions asked anymore.

Can anyone point me in the right direction to set these defaults, that will save me these annoyances?

---

### Post by aysiu on 2010-06-05
We need more details.

What filesystem is this new partition? Ext4? FAT32? NTFS? What does your /etc/fstab file look like?

How are these shared or network drives set up? Samba? NFS?

---

### Post by Moozillaaa on 2010-06-05
> **aysiu said:**
> We need more details.

What filesystem is this new partition? Ext4? FAT32? NTFS? What does your /etc/fstab file look like?

How are these shared or network drives set up? Samba? NFS?

Some are ext3, some ext2, some fat32, some ntfs...

I don't know if all are included in Samba share list by default or not, or if they're in nfs share list...

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdf5
UUID=5aff062a-5f40-4ab9-84d9-32b503af07b9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0chucknb@chucknb-desktop:~$ sudo fdisk -l
[sudo] password for chucknb: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb015a805

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       28046   184321777+  83  Linux
/dev/sda3           28047       28556     4096575   82  Linux swap / Solaris
/dev/sda4           28557       46403   143356027+  83  Linux

===================================

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37460703

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25496   204796588+  83  Linux
/dev/sdb2           25497       42706   138239325   83  Linux
/dev/sdb3           42707       60801   145348087+  83  Linux

=================================

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6f6f6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       25496   204796588+  83  Linux
/dev/sdc2           25497       42706   138239325   83  Linux
/dev/sdc3           42707       60801   145348087+  83  Linux

====================================

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x50395f2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       62005     1953125+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdd2           62006     3255210   100585938   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdd3         3255210     7752336   141659488   83  Linux
Partition 3 does not end on cylinder boundary.

=======================================

Disk /dev/sde: 250.0 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0xe2e1fadc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           2       62005     1953125+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sde2           62006     3255210   100585938   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sde3         3255210     7752336   141659488   83  Linux
Partition 3 does not end on cylinder boundary.

=========================================

Disk /dev/sdf: 250.0 GB, 250059349504 bytes
1 heads, 63 sectors/track, 7752335 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0xe2e1fadc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           2       62005     1953125+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdf2           62006     3255210   100585938   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdf3         3255210     7752336   141659488   83  Linux
Partition 3 does not end on cylinder boundary.

=============================================

Disk /dev/sdk: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35274212

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1            5100       28046   184321777+  83  Linux

================================

Disk /dev/sdl: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df049

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1   *       50994      101986   409601272+   7  HPFS/NTFS
/dev/sdl2          101987      182401   645933487+   7  HPFS/NTFS
/dev/sdl3               1       50993   409601241    7  HPFS/NTFS

Partition table entries are not in disk order

================================

Disk /dev/sdm: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38665b5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1               1       12766   102537216    7  HPFS/NTFS
/dev/sdm2           12766       30402   141659488    7  HPFS/NTFS
/dev/sdm3           30402      121602   732561408    f  W95 Ext'd (LBA)
/dev/sdm5           30402       94143   512000000    7  HPFS/NTFS
/dev/sdm6           94144      121601   220556353+   7  HPFS/NTFS
chucknb@chucknb-desktop:~$

---

### Post by Moozillaaa on 2010-06-06
Anybody know how to change settings here?

Logging in as root is a pain, just to change some files...

---

