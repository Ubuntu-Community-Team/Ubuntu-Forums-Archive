---
title: "Fat 32 problem"
date: 2006-07-30
forum: Desktop Environments
---

### Post by abrarey on 2006-07-30
Hi I recently installed ubuntu at home. I had a lot of time using it at the office.
I have 3 hard drives, one SATA my primary, 1 ATA and the other one is a USB hard drive.
in my ATA drive I have 2 partitions one NTFS and the other is FAT32. the problem is ubuntu doesnt read my FAT32 partition, it says its innacesible, here is a list of my hard drives.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080        7903    30716280    7  HPFS/NTFS
/dev/sda3            7904        8034     1052257+  82  Linux swap / Solaris
/dev/sda4            8035        9729    13615087+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1007     8088696    b  W95 FAT32
/dev/hdb2            1008        4997    32049675    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761408 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016    7  HPFS/NTFS

as u can see the partition is in the drive /dev/hdb1 I tried to format again the drive and nothing happens. in Windows I can acces the partition without problems. Dont undertand because ubuntu can read the NTFS without any problem.
here is my fstab.

proc            /proc           proc    defaults        0       0
/dev/sda4       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb2	/media/hdb2	ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1	/media/hdb1	vfat    umask=0000 0 0

need some help. thanks in advance.

---

### Post by spin2cool on 2006-07-30
Have you followed these instructions:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

Change your fstab to match - see if it works.

---

### Post by abrarey on 2006-07-31
I'd tried, but still not working.

Perhaps is something wrong with the hard drive i'll try repartiton an format the entire disk again to see what happens.

---

