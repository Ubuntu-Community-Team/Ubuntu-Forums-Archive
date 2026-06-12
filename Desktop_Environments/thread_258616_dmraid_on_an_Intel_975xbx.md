---
title: "dmraid on an Intel 975xbx"
date: 2006-09-16
forum: Desktop Environments
---

### Post by zerohope on 2006-09-16
I'm trying to get kubuntu to mount a ntfs raid-5 partition on the Intel SATA Raid controller (not the Si controller) on an Intel 975xbx (the OS see the drive on the Si controller just fine since it is only one drive and not set up as raid). Anyway...

First fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4650    37351093+  83  Linux
/dev/sda2            4651        4905     2048287+  82  Linux swap / Solaris
/dev/sda3            4906       30401   204796620    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdd doesn't contain a valid partition table

editing the fstab with the line

/dev/sdb1 /media/sdb1 ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0

doesn't work.

So next I installed dmraid

sudo apt-get install dmraid

and everything appears to install correctly

Next I try, dmraid -s

/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
*** Active Set
name   : nvidia_edcbefij
size   : 488397166
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_bggbfdbhde
--> Subset
name   : isw_bggbfdbhde_Volume0
size   : 976783878
stride : 128
type   : raid5
status : ok
subsets: 0
devs   : 3
spares : 0

next dmraid - ay -v

/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_edcbefij" already active
INFO: Activating stripe RAID set "nvidia_edcbefij"
ERROR: Unsupported RAID type raid5[512] on isw_bggbfdbhde_Volume0
ERROR: no mapping possible for RAID set isw_bggbfdbhde_Volume0
INFO: Activating GROUP RAID set "isw_bggbfdbhde"
RAID set "nvidia_edcbefij1" already active
INFO: Activating partition RAID set "nvidia_edcbefij1"
RAID set "nvidia_edcbefij2" already active
INFO: Activating partition RAID set "nvidia_edcbefij2"
RAID set "nvidia_edcbefij3" already active
INFO: Activating partition RAID set "nvidia_edcbefij3"

If I try

root@linux-pc:/home/brett# sudo mount /dev/mapper/isw_bggbfdbhde_Volume0 /media/sdb1 -t ntfs
mount: special device /dev/mapper/isw_bggbfdbhde_Volume0 does not exist

it is a no go...

I've searched all over and haven't been able to find anything definitive on how to get this to work. I checked out the FakeRaid thing, but I'm not trying to boot from the raid array, I just want to be able to read and write to the ntfs partition on it. Surely I can't be the only person in the world trying to do this with a 975xbx, could I? :confused:

---

