---
title: "LILO not working with root-LVM-RAID setup"
date: 2007-04-29
forum: Desktop Environments
---

### Post by gregturn on 2007-04-29
I upgraded from Edgy to Feisty last week, and LILO no longer seems able to write an updated MBR. I'm currently running a root-on-LVM-on-RAID configuration that seemed to work fine on Edgy, but went awry when I upgraded to Feisty using the Upgrade Manager.

Configuration:
```

gregturn@startrek:~$ uname -a
Linux startrek 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

gregturn@startrek:~$ mount
/dev/mapper/startrekvg-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-386/volatile type tmpfs (rw)
/dev/mapper/startrekvg-boot on /boot type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

Error message from LILO:
```

gregturn@startrek:~$ sudo lilo
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/.nodes/hdd1'
Fatal: is_primary:  Not a valid device  0xFE00

```

/proc/partitions:
```

gregturn@startrek:~$ cat /proc/partitions 
major minor  #blocks  name

  22     0  156290904 hdc
  22     1  156288321 hdc1
  22    64  156290904 hdd
  22    65  156288321 hdd1
   9     0  156288256 md0
 254     0  156288321 dm-0
 254     1  156288321 dm-1
 254     2     102400 dm-2
 254     3  155660288 dm-3
 254     4     524288 dm-4
 254     5     524288 dm-5
 254     6     102400 dm-6
 254     7  155660288 dm-7

```

I checked the RAID cluster to see if everything was okay.

```

gregturn@startrek:~$ sudo mdadm --misc --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Mar 31 16:30:39 2007
     Raid Level : raid1
     Array Size : 156288256 (149.05 GiB 160.04 GB)
    Device Size : 156288256 (149.05 GiB 160.04 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Apr 29 14:55:03 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 30f49850:949309ee:8c553fec:62cb732e
         Events : 0.236991

    Number   Major   Minor   RaidDevice State
       0     254        0        0      active sync   /dev/mapper/hdd1
       1     254        1        1      active sync   /dev/mapper/hdc1

```

I thought it a little strange that /dev/mapper held the names of my hard drives. It should just be /dev/hdc1 and /dev/hdd1. At least it was when edgy was running.

I removed the device files from /dev/evms/.nodes, and recreated them directly in /dev. Well, mdadm reported the correct path names of my devices. But I tried to run LILO again, and it didn't work!
```

gregturn@startrek:/dev/evms/.nodes$ sudo mv hdc1 /dev
gregturn@startrek:/dev/evms/.nodes$ sudo mv hdd1 /dev
gregturn@startrek:/dev/evms/.nodes$ sudo mdadm --misc --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Mar 31 16:30:39 2007
     Raid Level : raid1
     Array Size : 156288256 (149.05 GiB 160.04 GB)
    Device Size : 156288256 (149.05 GiB 160.04 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Apr 29 15:10:17 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 30f49850:949309ee:8c553fec:62cb732e
         Events : 0.236991

    Number   Major   Minor   RaidDevice State
       0     254        0        0      active sync   /dev/hdd1
       1     254        1        1      active sync   /dev/hdc1
gregturn@startrek:/dev/evms/.nodes$ sudo lilo
Fatal: cache_add: LILO internal error

```
I moved the device files back to /dev/evms/.nodes, stopped & started udev, and LILO is back to reporting the original error.

I'm beginning to suspect that LILO isn't at fault here, but instead showing symptons of a different problem.

The readout from /proc/mdstat is as follows:
```

gregturn@startrek:~$ cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 dm-1[1] dm-0[0]
      156288256 blocks [2/2] [UU]
      
unused devices: <none>

```

One other possibility is the fact that when I set everything up under edgy, I had the hard drives plugged in to IDE0, which made them /dev/hda1 and /dev/hdb1. In order to hook up my CD-ROM drives and due to cable lengths and locations in the housing. I moved them to IDE1, making them /dev/hdc1 and /dev/hdd1. Since everything else seems to boot okay, doesn't like that should be a problem.

I can't tell who is the culprit here! LILO won't install a properly upgraded MBR for me, so I have to manually enter extra commands any time I reboot this machine. This is tough to search google, because evms, raid, dm, and lilo all turn up info way too general. I tried LILO's error message in google with several options, and got nothing of use. Is there some more information I can go dig up on my system that would help anyone?

Thanks for any light you can help me shed on this.

---

### Post by nicolasr on 2007-04-30
Hello Gregturn,

No light to shed, but I walk in the dark with you. I mean : same exact every problem :-(

I wish someone knows how to fix this, because as you said it's a pain in the *** to google for this problem...

nicolasr

---

### Post by gregturn on 2007-05-01
Some updated information. I have tried filing a bug report on launchpad.net. Based on another bug report, I have dumped out /proc/mount:
```

gregturn@startrek:/dev/mapper$ cat /proc/mounts 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
/dev/mapper/startrekvg-root / ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-15-386/volatile tmpfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/mapper/startrekvg-boot /boot ext3 rw,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/mapper/startrekvg-root /dev/.static/dev ext3 rw,data=ordered 0 0
udev /dev tmpfs rw 0 0

```
Strangely, it appears my root logical volume is mounted in two places, / and /dev/.static/dev.  What causes that? I tried umount /dev/.static/dev, but still get same error when trying to run LILO.

The bug report I filed is at [https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/111406](https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/111406)

---

### Post by gregturn on 2007-05-05
I re-reran LILO with "-v5" to get more details about this failure to run on Feisty.

```

gregturn@startrek:/boot$ sudo lilo -v5
LILO version 22.6.1, Copyright (C) 1992-1998 Werner Almesberger
Development beyond version 21 Copyright (C) 1999-2004 John Coffman
Released 17-Nov-2004, and compiled at 13:54:18 on Mar 7 2007
Ubuntu

Warning: LBA32 addressing assumed
raid_setup: dev=0011 rdev=0900
pf_hard_disk_scan: (22,0) /dev/hdc
pf_hard_disk_scan: (22,1) /dev/hdc1
lookup_dev: number=1600
lookup_dev: number=1600
pf: dev=1600 id=00022E56 name=/dev/hdc
geo_query_dev: device=1600
lookup_dev: number=1600
lookup_dev: number=0300
exit geo_query_dev
bios_dev: device 1600
lookup_dev: number=1600
bios_dev: masked device 1600, which is /dev/hdc
bios_dev: geometry check found 0 matches
bios_dev: (0x81) vol-ID=0003CA77 *PT=080778B6
bios_dev: (0x80) vol-ID=00022E56 *PT=0807786E
bios_dev: PT match found 1 match (0x80)
pf_hard_disk_scan: (22,64) /dev/hdd
pf_hard_disk_scan: (22,65) /dev/hdd1
lookup_dev: number=1640
lookup_dev: number=1640
pf: dev=1640 id=0003CA77 name=/dev/hdd
geo_query_dev: device=1640
lookup_dev: number=1640
exit geo_query_dev
bios_dev: device 1640
lookup_dev: number=1640
bios_dev: masked device 1640, which is /dev/hdd
bios_dev: geometry check found 0 matches
bios_dev: (0x81) vol-ID=0003CA77 *PT=080778B6
bios_dev: (0x80) vol-ID=00022E56 *PT=0807786E
bios_dev: PT match found 1 match (0x81)
pf_hard_disk_scan: (9,0) /dev/md0
pf_hard_disk_scan: (254,0) /dev/dm-0
lookup_dev: number=FE00
Caching device /dev/evms/.nodes/hdd1 (0xFE00)
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/.nodes/hdd1'
pf_hard_disk_scan: (254,1) /dev/dm-1
lookup_dev: number=FE01
Caching device /dev/evms/.nodes/hdc1 (0xFE01)
    Name change: '/dev/dm-1' -> '/dev/evms/.nodes/hdc1'
pf_hard_disk_scan: (254,2) /dev/dm-2
lookup_dev: number=FE02
Caching device /dev/evms/lvm2/startrekvg/boot (0xFE02)
    Name change: '/dev/dm-2' -> '/dev/evms/lvm2/startrekvg/boot'
pf_hard_disk_scan: (254,3) /dev/dm-3
lookup_dev: number=FE03
Caching device /dev/evms/lvm2/startrekvg/root (0xFE03)
    Name change: '/dev/dm-3' -> '/dev/evms/lvm2/startrekvg/root'
pf_hard_disk_scan: (254,4) /dev/dm-4
lookup_dev: number=FE04
Caching device /dev/evms/lvm2/startrekvg/swap (0xFE04)
    Name change: '/dev/dm-4' -> '/dev/evms/lvm2/startrekvg/swap'
pf_hard_disk_scan: (254,5) /dev/dm-5
lookup_dev: number=FE05
Caching device /dev/mapper/startrekvg-swap (0xFE05)
    Name change: '/dev/dm-5' -> '/dev/mapper/startrekvg-swap'
pf_hard_disk_scan: (254,6) /dev/dm-6
lookup_dev: number=FE06
Caching device /dev/mapper/startrekvg-boot (0xFE06)
    Name change: '/dev/dm-6' -> '/dev/mapper/startrekvg-boot'
pf_hard_disk_scan: (254,7) /dev/dm-7
lookup_dev: number=FE07
Caching device /dev/mapper/startrekvg-root (0xFE07)
    Name change: '/dev/dm-7' -> '/dev/mapper/startrekvg-root'
  1600 00022E56 /dev/hdc
  1640 0003CA77 /dev/hdd
pf_hard_disk_scan: ndevs=2
  1600 00022E56 /dev/hdc
  1640 0003CA77 /dev/hdd
Resolve invalid VolumeIDs
Resolve duplicate VolumeIDs
  1600 00022E56 /dev/hdc
  1640 0003CA77 /dev/hdd
device codes (user assigned pf) = 0
device codes (user assigned) = 0
device codes (BIOS assigned) = 3
device codes (canonical) = 3
lookup_dev: number=0900
RAID info: nr=2, raid=2, active=2, working=2, failed=0, spare=0
md: RAIDset device 0 = 0xFE00
lookup_dev: number=FE00
lookup_dev: number=FE00
geo_get: device 1640, all=1
geo_query_dev: device=1640
lookup_dev: number=1640
exit geo_query_dev
bios_dev: device 1640
lookup_dev: number=1640
bios_dev: masked device 1640, which is /dev/hdd
bios_dev: geometry check found 0 matches
bios_dev: (0x81) vol-ID=0003CA77 *PT=080778B6
bios_dev: (0x80) vol-ID=00022E56 *PT=0807786E
bios_dev: PT match found 1 match (0x81)
Device 0x1640: BIOS drive 0x81, 255 heads, 19457 cylinders,
               63 sectors. Partition offset: 0 sectors.
registering bios=0x81 device=0x1640
Using Volume ID 0003CA77 on bios 81
RAID scan: geo_get: returns geo->device = 0x81 for device FE00
Fatal: is_primary: Not a valid device 0xFE00

```

---

### Post by gregturn on 2007-06-07
For the record, I threw in the towel and reloaded feisty on the machine on top of LVM on top of RAID-1. It works now. Hope that doesn't happen again.

---

