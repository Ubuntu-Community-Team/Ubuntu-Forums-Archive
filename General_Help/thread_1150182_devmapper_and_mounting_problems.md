---
title: "dev/mapper and mounting problems"
date: 2009-05-05
forum: General Help
---

### Post by ant2ne on 2009-05-05
[Jump to post #4, reference post #1-3 as history.]("http://ubuntuforums.org/showpost.php?p=7247092&postcount=4")


raid worked before upgrade.
```
ant2ne@2ne-buntu:~$ ls /dev/mapper/nv*
/dev/mapper/nvidia_ccfhebia   /dev/mapper/nvidia_ccfhebia5
/dev/mapper/nvidia_ccfhebia1  /dev/mapper/nvidia_ccfhebia6
/dev/mapper/nvidia_ccfhebia2
ant2ne@2ne-buntu:~$ sudo mount -t ext3 /dev/nvidia_ccfhebia6 /media/md3
mount: special device /dev/nvidia_ccfhebia6 does not exist
ant2ne@2ne-buntu:~$ 
```note: /media/md3 is the old mount point, and if I don't remount it there other things will break.

Edit, running this script
> #!/bin/sh
date >> /home/ant2ne/RAID1Status
#ls /dev/md* >> ~/RAID1Status
cat /proc/mdstat | grep active >> ~/RAID1Status

Results in
> Tue May  5 20:54:37 CDT 2009
md3 : inactive dm-4[1](S)
md2 : active raid1 dm-3[1]
md0 : inactive dm-1[1](S)
md1 : active raid1 dm-2[1]


md0 is my swap (no big worry right now) but md3 is my data and shares. How do I reactivate them?

---

### Post by ant2ne on 2009-05-09
> ant2ne@2ne-buntu:~$ sudo e2fsck -b 8193 /dev/md3
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Invalid argument while trying to open /dev/md3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Using gparted I can see /dev/md3 and it claims to have data written on it. if I use gparted to check the drive errors on "Filesystem mounted or opened exclusively by another program?" I can't find any place it is mountd.

---

### Post by ant2ne on 2009-05-09
sudo mdadm -R /dev/md3 started the array and I was able to then mount it. I can access my data.

Observing sudo mdadm -D /dev/mdX of all the arrays it appears that one drive is missing. This drive was working just fine before my OS re-install. That leads me to believe the drive is functional, but just not cooperating. In a moment I will pop open the case and re-examine its physical connections. EDIT: did this, device seems connected and functional.

md0 (swap)
```
ant2ne@2ne-buntu:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat May  2 22:54:25 2009
     Raid Level : raid1
     Array Size : 7815488 (7.45 GiB 8.00 GB)
  Used Dev Size : 7815488 (7.45 GiB 8.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May  3 00:06:43 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : d0c0c97b:efa76a67:014ae0c2:d6f16d1e
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        1        1      active sync   /dev/block/252:1

```

md1 (/)
```
ant2ne@2ne-buntu:~$ sudo mdadm -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Sat May  2 22:54:35 2009
     Raid Level : raid1
     Array Size : 117186048 (111.76 GiB 120.00 GB)
  Used Dev Size : 117186048 (111.76 GiB 120.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat May  9 13:54:56 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 50b4202e:9fceb45c:a2e798ed:f052b48c
         Events : 0.2577

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        2        1      active sync   /dev/block/252:2
ant2ne@2ne-buntu:~$ 

```

md2 (homes)
```
ant2ne@2ne-buntu:~$ sudo mdadm -D /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Sat May  2 22:56:21 2009
     Raid Level : raid1
     Array Size : 117185984 (111.76 GiB 120.00 GB)
  Used Dev Size : 117185984 (111.76 GiB 120.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat May  9 13:55:16 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : f45d91d0:92b92099:dc69729a:aff78073
         Events : 0.3416

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        3        1      active sync   /dev/block/252:3

```



md3
```
ant2ne@2ne-buntu:~$ sudo mdadm -D /dev/md3
/dev/md3:
        Version : 00.90
  Creation Time : Sat May  2 23:10:11 2009
     Raid Level : raid1
     Array Size : 490384000 (467.67 GiB 502.15 GB)
  Used Dev Size : 490384000 (467.67 GiB 502.15 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Sat May  9 13:52:34 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : e3ef7177:8ec091e7:2c96ad3c:b504de45
         Events : 0.20

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        4        1      active sync   /dev/block/252:4
ant2ne@2ne-buntu:~$ 
```

Assuming that the drive is physically functional: I will need to figure out how to make the drivers begin to mirror again. Any advice on how to proceed?

---

### Post by ant2ne on 2009-05-09
OK Now I'm confused.

I powered down. Pulled a drive and powered back up. "sudo mdadm -D /dev/md3" exact same results (as posted above.) 

```
ant2ne@2ne-buntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 dm-1[1]
      7815488 blocks [2/1] [_U]
      
md2 : active raid1 dm-3[1]
      117185984 blocks [2/1] [_U]
      
md3 : active raid1 dm-4[1]
      490384000 blocks [2/1] [_U]
      
md1 : active raid1 dm-2[1]
      117186048 blocks [2/1] [_U]
      
unused devices: <none>
```

I powered down again. replaced the drive and yanked the other one. Then I powered back up. "sudo mdadm -D /dev/md3" exact same results (as posted above.) "cat /proc/mdstat" exact same results.

IS IT POSSIBLE THAT MY RAID IS FUNCTIONING PROPERLY AND THIS IS ALL A BUG?

I made some changes on the hard drive. Powered down, unplugged a drive and powered back up changes stuck. Powered down, unplugged other drive and plugged in the unplugged. Powered up and changes stuck. Powered down and replugged both drives. RAID1 seems functional on both drives, but doesn't seem to be reporting correctly.

---

### Post by tboydva on 2009-05-11
Ant2ne,

I have the same problem (although a little less complicated). I have a home server and had a power outage when upgrading from 8.1 to 9.01. I finally decided to wipe they system and reload. My system is in the basement and I have an old crappy keyboard and the enter key stuck when reloading. Anyway, at some point, I selected LVM (which AFAIK, I haven't used in the past). I should admit that I set up everything 10 years ago - and I only start searching for help when it breaks (a reasonable testament to linux server). Anyhow, in researching this issue (I get a "clean, degraded" state just like you with /dev/block/252:1 to describe my device instead of /dev/sdxx), I seem to remember seeing some reference to LVM? I haven't tried removing any drives yet (I have a two disk RAID 1 array), but so far, I've been unable to fix the degraded state. Maybe there's some issue with logical management? Just a thought?
TJB

---

### Post by ant2ne on 2009-05-16
I don't recall configuring anything for LVM maybe that is my problem.

---

### Post by ant2ne on 2009-05-20
bump

---

### Post by ant2ne on 2009-05-25
bump

---

