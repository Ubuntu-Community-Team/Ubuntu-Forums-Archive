---
title: "Can't create raid array. drive is always busy"
date: 2009-06-14
forum: General Help
---

### Post by iLLNiSS on 2009-06-14
I previously had a raid array consisting of 2x 1TB drives, and 2x 500GB drives, 6 partitions total.

I upgraded the 500gb drives and started fresh. I was intending to use 1TB partition sizes (well close, you get the idea) so killing the array one drive at a time was not worth it.

so anyways, I pop out the 2x 500gb drives, insert the new 1TB's, they format fine etc etc...

now the problem starts here. my pre existing 1TB drives would refuse to do anything. formatting with gparted errors out. i booted from a live cd to format the partitions, boot back to my os to create the array but mdadm complains the drive is already in use and cant create the array

theres nothing i can see mounting the partition.. no app is using the drive. auto mount has been disabled.. ive tried everything i can read on google and nothing is working..

is there anyone who has a for sure way to detect what is causing this?

```

server@server-basement:~$ sudo mkfs.ext3 -L "" /dev/sdc1
[sudo] password for server: 
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdc1 is apparently in use by the system; will not make a filesystem here!
server@server-basement:~$ sudo fdisk -l /dev/sdc1

Disk /dev/sdc1: 1000.1 GB, 1000103537664 bytes
255 heads, 63 sectors/track, 121588 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc1 doesn't contain a valid partition table
server@server-basement:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
server@server-basement:~$ sudo mdadm --create /dev/md0 --chunk=64 --level=5 --raid-devices=4 --auto=md /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=976663608K  mtime=Sun Jun 14 00:14:22 2009
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=976663608K  mtime=Sun Jun 14 00:14:33 2009
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=976655576K  mtime=Sun Jun 14 00:14:20 2009
mdadm: create aborted
server@server-basement:~$ sudo mdadm --examine /dev/sdc1mdadm: No md superblock detected on /dev/sdc1.
server@server-basement:~$ sudo lsof /dev/sdc1lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/server/.gvfs
      Output information may be incomplete.
server@server-basement:~$ sudo umount /dev/sdc1umount: /dev/sdc1: not mounted
server@server-basement:~$ sudo mount /dev/sdc1 /media/TEMP123mount: /dev/sdc1 already mounted or /media/TEMP123 busy
server@server-basement:~$ sudo fuser -v /dev/sdc1
server@server-basement:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1a64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121589   976663611   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0716

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121589   976663611   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000002

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121589   976663611   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d664

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121589   976663611    b  W95 FAT32

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffda6e4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   83  Linux

Disk /dev/sdf: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a4a6971

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        2432    19535008+  83  Linux
/dev/sdf2            2433       34049   253963552+   5  Extended
/dev/sdf5            2433        2918     3903763+  82  Linux swap / Solaris
/dev/sdf6            2919       34049   250059726   83  Linux
server@server-basement:~$ sudo mdadm --detail /dev/md0mdadm: md device /dev/md0 does not appear to be active.
server@server-basement:~$ sudo mdadm --create /dev/md0 --chunk=64 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=976663608K  mtime=Sun Jun 14 00:14:22 2009
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=976663608K  mtime=Sun Jun 14 00:14:33 2009
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=976655576K  mtime=Sun Jun 14 00:14:20 2009
mdadm: create aborted

```

this is right after i formatted the drive in a live cd environment.. in that live environment i was able to create and delete files/dirs on the disk no problem.. but something in my actual install wont allow it.. i was running 8.10 but today upgraded to 9.04 which is actually when /dev/sdd1 came alive...

---

### Post by iLLNiSS on 2009-06-14
any help is appreciated... ive got no direction on this anymore as i cant read anything to try.. ive exhausted all possible ideas and fixes for other people

---

### Post by iLLNiSS on 2009-06-14
PROBLEM SOLVED!

turns out my sata controller was tying the drive up.. it had both of the old 1TB drives reserved.. dont know why only one never worked. either way did a quick format in the sata controller bios and it freed them up all is well now :) got the solution partly from someones blog post. he said nvraid was tying his drives up completely. i checked my onboard it was disabled but my external ones were.

off to building my 4 drive raid then expanding with the backup drives yay :)

---

### Post by fjgaude on 2009-06-14
Well, whatever your array was called, stop it using **mdadm**. Then to each drive zero the superblocks, one at a time, like so:

```
sudo mdadm --zero-superblack /dev/sd[nn]
```

Then the drives will be free. The drives without doing that are shown in mdadm as still being part of an active array.

Lots to learn when using software raid, eh?

---

### Post by iLLNiSS on 2009-06-15
well, onto a new problem. 

i went ahead and created the array fresh with 3 drives instead of 4 as i couldnt get the one drive freed up again (before i seen your post.. which i have yet to try)... and i copied my data over..

well, upon reboot the array stopped working, and now im in the midst of rebuilding.. well.. while rebuilding i get to %2 or so, then the detail shows the array completely differently from before.r

EDIT: i just tried zeroing the superblock on the busy drive and it fails. examine in mdadm still shows the drive fine though

```

server@server-basement:/media/raid5$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jun 15 16:58:00 2009
     Raid Level : raid5
     Array Size : 1953326976 (1862.84 GiB 2000.21 GB)
  Used Dev Size : 976663488 (931.42 GiB 1000.10 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jun 15 17:08:52 2009
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 2% complete

           UUID : f942c615:2086fed0:ba9c2746:b85566bc (local to host server-basement)
         Events : 0.26

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       4       8       65        1      spare rebuilding   /dev/sde1
       2       8       49        2      active sync   /dev/sdd1

       3       8       17        -      spare   /dev/sdb1
server@server-basement:/media/raid5$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jun 15 16:58:00 2009
     Raid Level : raid5
     Array Size : 1953326976 (1862.84 GiB 2000.21 GB)
  Used Dev Size : 976663488 (931.42 GiB 1000.10 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jun 15 17:11:49 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f942c615:2086fed0:ba9c2746:b85566bc (local to host server-basement)
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       0        0        2      removed

       3       8       17        -      spare   /dev/sdb1
       4       8       65        -      spare   /dev/sde1
       5       8       49        -      faulty spare   /dev/sdd1
server@server-basement:/media/raid5$ 

```what is going on here?

---

