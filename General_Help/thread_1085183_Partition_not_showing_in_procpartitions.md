---
title: "Partition not showing in /proc/partitions"
date: 2009-03-02
forum: General Help
---

### Post by kilroy423 on 2009-03-02
Hey everyone,

I have been having some interesting problems lately on my file server.  I have a software raid 5(xfs) setup on 4 drives.  This raid hasn't been auto starting on reboots, although it used to.  It appears that the problem is that my /dev/sdd1, is not appearing in /proc/partitions.  The drive appears in /proc/partitions, but not the partition.  The fun thing is that fdisk /dev/sdd shows that it has a partition table with the correct partition.  Any ideas?

Thanks!

---

### Post by lensman3 on 2009-03-02
This is really fishing!!!  I had a MB where the BIOS had to be set just right for Linux to even see the disk and boot.  Is the bios for this disk set wrong.

Also if you do a "lspci -vv", can this program see or tell you anything about the disk hardware?  What does "hdparm" tell you about the disk?

Sorry I'm not more help, but it sounds like a MB/BIOS problem.

---

### Post by kilroy423 on 2009-03-02
This is really odd.  I have never seen this...here is some more info.

```
dan@server:~$ cat /proc/partitions
major minor  #blocks  name

   8     0    9770544 sda
   8     1    3678853 sda1
   8     2          1 sda2
   8     5     224878 sda5
   8    16  625131864 sdb
   8    17  625129281 sdb1
   8    32  488386584 sdc
   8    33  488384001 sdc1
   8    48  488386584 sdd  <-----
   8    64  488386584 sde
   8    65  488384001 sde1
   8    80  488386584 sdf
   8    81  488384001 sdf1

```

```
dan@server:~$ sudo fdisk /dev/sdd
[sudo] password for dan:

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06b01b52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

```

```
dan@server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdc1[0](S) sdf1[3](S) sdd[2](S) sde1[1](S)
      1953538304 blocks

unused devices: <none>

```

The bios hasn't been changed...I first thought that the drive was failing, but passed smart with flying colors.  In order for me to readd the drive back to the raid, I have to delete the partition, create a new partition, and then readd to the array.  I have dd'ed over the begin of the drive with zeros in hopes that it might help.  The odd thing is that if there was a major hardware issue, then it wouldn't see the drive at all, much less let me create a new partition...???

---

