---
title: "Harddrive  analyse info"
date: 2009-04-16
forum: General Help
---

### Post by wilcan34 on 2009-04-16
Installed xp first instlled itself on 6G drive.
Installed Ubuntu on 27G Drive.
Prefer Ubuntu but need xp to run VCarve ProCNC programme.
Am getting a lot of freezing on the 6G and had a look at the setup in Gparted.
6G should be enough to run xp.
Could some one advise on what I am seeing?
Thank You
Regards
G




reg@greg-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              27G  3.7G   22G  15% /
varrun                363M   92K  363M   1% /var/run
varlock               363M     0  363M   0% /var/lock
udev                  363M   84K  363M   1% /dev
devshm                363M     0  363M   0% /dev/shm
lrm                   363M   40M  324M  11% /lib/modules/2.6.24-23-386/volatile
greg@greg-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=57fec3e8-0370-416f-96a4-ff2da00d3973 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=3862b44c-1caf-4d35-8cdb-debfa7de17f3 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
greg@greg-desktop:~$ sudo blkid
/dev/sda1: UUID="34FCBCE0FCBC9E14" TYPE="ntfs" 
/dev/sda5: TYPE="swap" 
/dev/sdb1: UUID="57fec3e8-0370-416f-96a4-ff2da00d3973" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="3862b44c-1caf-4d35-8cdb-debfa7de17f3" 
greg@greg-desktop:~$ sudo fdisk -l

Disk /dev/sda: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86070c77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         752     6040408+   7  HPFS/NTFS
/dev/sda2             753         788      289170    5  Extended
/dev/sda5             753         788      289138+  82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005fe8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3495    28073556   83  Linux
/dev/sdb2            3496        3647     1220940    5  Extended
/dev/sdb5            3496        3647     1220908+  82  Linux swap / Solaris
greg@greg-desktop:~$

---

### Post by wilcan34 on 2009-04-16
Sorry,guess its the yellow triangle.What is it and is it stopping to reformat?
G

---

### Post by belikralj on 2009-04-16
I'm not sure what the exact reason is but i found the same thing and it disappeared after I got the  'ntfs-3g'  package installed through synaptic. You may also find  'ntfs-config'  a useful tool when using windows partitions.

---

### Post by Ticketoride on 2009-04-16
> Installed xp first instlled itself on 6G drive.
Might get away with a minimnal bare-bone install ... usually takes about 7.5 GB with Drivers. You might have run out Disk Space.

---

