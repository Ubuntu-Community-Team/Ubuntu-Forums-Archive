---
title: "upgrade reordered drives, confused software raid-1"
date: 2009-01-19
forum: General Help
---

### Post by LazyBoy on 2009-01-19
I recently upgraded a box from 7.4 to 7.10, then then 8.4.
Now I've noticed that my drives got reordered (probably
a SATA driver change) and my RAID-1 is degraded.
 
My (PATA) OS drive had some other partitions and *was* 
known as /dev/sda.
My (SATA) raid-1 /home *was* made from /dev/sdb and 
/dev/sdc.

**Now** my OS drive is sdc with side effects like mounting 
some sdc partitions on my old sda mount points.  (not a big deal)

> 
mastershake:~> df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc5             10080488   2811616   6756804  30% /
varrun                  192668       372    192296   1% /var/run
varlock                 192668         0    192668   0% /var/lock
udev                    192668        88    192580   1% /dev
devshm                  192668         0    192668   0% /dev/shm
lrm                     192668     39792    152876  21% /lib/modules/2.6.24-23-generic/volatile
/dev/sdc1              7158988   5118964   2040024  72% /media/sda1
/dev/sdc7             20295680   2210736  17053976  12% /media/sda7
/dev/md0             240362560 157387480  70765288  69% /home



The real problem is the RAID-1.  I think the following 3
queries say:
1) the raid is running with SDA, with the other drive removed.
2) SDA is clean and part of md0
3) SDB is "clean", but part of a raid that doesn't exist.


> 
mastershake:~> sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Jan  2 12:53:01 2005
     Raid Level : raid1
     Array Size : 244195904 (232.88 GiB 250.06 GB)
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan 18 23:33:56 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 61645020:223a69dc:12d77363:0c0f047d
         Events : 0.5125062

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed



> 
mastershake:~> sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 61645020:223a69dc:12d77363:0c0f047d
  Creation Time : Sun Jan  2 12:53:01 2005
     Raid Level : raid1
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Sun Jan 18 23:34:36 2009
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : e627430d - correct
         Events : 0.5125064


      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed



> 
mastershake:~> sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 61645020:223a69dc:12d77363:0c0f047d
  Creation Time : Sun Jan  2 12:53:01 2005
     Raid Level : raid1
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Sep 16 07:38:13 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e5808830 - correct
         Events : 0.5048904


      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1



I've definitely touched files, so SDB is actually dirty.

So what's the safest way to fix this?  I've never had
to rebuild before.

Thanks,
LB

---

### Post by LazyBoy on 2009-01-19
Also, why didn't the use of UUIDs instead of partition references avoid this??

> 
mastershake:/proc> cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0]
      244195904 blocks [2/1] [U_]
      
unused devices: <none>



> 
mastershake:/etc/mdadm> cat mdadm.conf
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=61645020:223a69dc:12d77363:0c0f047d

# This file was auto-generated on Fri, 20 Jul 2007 23:50:16 -0400
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $


Thanks,
LB

---

### Post by justtech on 2009-01-19
Did you ever get this figured out?  I think I might have a similar problem and can't get my RAID drives to mount either.... just curious.

---

