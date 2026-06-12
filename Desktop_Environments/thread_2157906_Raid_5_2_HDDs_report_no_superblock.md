---
title: "Raid 5 2 HDDs report no superblock"
date: 2013-06-27
forum: Desktop Environments
---

### Post by bigsuccess on 2013-06-27
Hi there,

I went on holiday and came back to my computer. I wanted to get the data off from 2 arrays which were plugged into the computer. One was fine, the other not so fine.

I check the drives
```

root@heavy:~# mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 52ba30ac:3bfacbbd:3c18857e:c000f821 (local to host heavy)
  Creation Time : Mon Jun  6 15:02:29 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540416 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Wed Dec 26 11:06:16 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 473330c5 - correct
         Events : 50031

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       80        1      active sync

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       80        1      active sync
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
```
```

root@heavy:~# mdadm --examine /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 52ba30ac:3bfacbbd:3c18857e:c000f821 (local to host heavy)
  Creation Time : Mon Jun  6 15:02:29 2011
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540416 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Wed Dec 26 11:06:16 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 473330a7 - correct
         Events : 50031

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       80        1      active sync
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
```

Running mdadm --examine on the other 2 drives simply stated there is no superblock.

I check the drives are available.. seems legit
```

root@heavy:~# fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00048016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    51730431    25761792    7  HPFS/NTFS/exFAT
/dev/sda3       113326080   117229567     1951744   82  Linux swap / Solaris
/dev/sda4   *    51730432   113326079    30797824   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0bbe1199

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
```

I check mdadm.conf is fine.. again, seems ok.
```

root@heavy:~# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=52ba30ac:3bfacbbd:3c18857e:c000f821 devices=/dev/sdb,/dev/sdc,/dev/sdd,/dev/sde
#ARRAY /dev/md2 devices=/dev/sdf,/dev/sde,/dev/sdd,/dev/sdc UUID=52ba30ac:3bfacbbd:3c18857e:c000f821

# This file was auto-generated on Wed, 29 Aug 2012 21:38:32 +1000
# by mkconf $Id$

```

Nothing seemed to get this working so I read some threads about re-creating the raid superblock information on each disk.

So then I tried this:
```
mdadm --create --assume-clean -vv /dev/md2 -n 4 -l 5 --chunk 64 --metadata=0.9 /dev/sdc /dev/sde /dev/sdd /dev/sdb
```

I can't mount the volume so I tried an alternate array create order:

```
root@heavy:~# mdadm --create --assume-clean -vv /dev/md2 -n 4 -l 5 --chunk 64 --metadata=0.9 /dev/sde /dev/sdb /dev/sdc /dev/sdd
mdadm: layout defaults to left-symmetric
mdadm: /dev/sde appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jun 27 19:54:27 2013
mdadm: /dev/sdb appears to contain an ext2fs file system
    size=1297137664K  mtime=Mon Jun 13 14:42:50 2011
mdadm: /dev/sdb appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jun 27 19:54:27 2013
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jun 27 19:54:27 2013
mdadm: /dev/sdd appears to contain an ext2fs file system
    size=1565573120K  mtime=Mon Jun 13 14:27:20 2011
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jun 27 19:54:27 2013
mdadm: size set to 1953513408K
Continue creating array? y
mdadm: array /dev/md2 started.
root@heavy:~# fsck.ext3  /dev/md2
e2fsck 1.42 (29-Nov-2011)
fsck.ext3: Superblock invalid, trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>? cancelled!

fsck.ext3: Illegal inode number while checking ext3 journal for eidetic

eidetic: ***** FILE SYSTEM WAS MODIFIED *****

eidetic: ********** WARNING: Filesystem still has errors **********
```

Why this seemed to say file system modified after ctrl c im not sure.. :\


What do?

---

### Post by bigsuccess on 2013-06-28
Can any RAID gurus help me please??

---

