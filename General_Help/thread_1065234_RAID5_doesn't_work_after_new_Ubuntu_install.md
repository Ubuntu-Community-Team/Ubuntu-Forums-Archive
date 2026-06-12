---
title: "RAID5 doesn't work after new Ubuntu install"
date: 2009-02-09
forum: General Help
---

### Post by Kilbasar on 2009-02-09
I just re-installed my system. I completely wiped all (system) partitions and started from scratch. My media (music/pics/etc) is stored on a separate RAID5 array. This was created using mdadm, and the mdadm.conf was auto-generated. After my system re-isntall, i re-installed mdadm, and rebooted. It immediately recognized my disks, and 'mdadm --detail /dev/md0' showed that it thought the array was degraded. It then proceeded to rebuild it. I didn't want to mess with it, so I let it finish. It now says everything is fine, except it doesn't see my ext3 partition on there. The only commands I've run so far are 'mdadm --assemble', 'mdadm --detail', and 'mdadm --stop'. I haven't changed anything, so my data must still be there, but I can't figure out why it doesn't see my ext3 partitions. Thanks!

```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr  2 16:08:44 2008
     Raid Level : raid5
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Feb  9 18:00:13 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 28ce99d8:12dc7f14:80dcd6ba:f1e671fb
         Events : 0.22

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       64        2      active sync   /dev/sde
```


```
# mount -t ext3 /dev/md0 /raid
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
# dmesg|tail
[36639.587123] raid5: device sdc operational as raid disk 1
[36639.588290] raid5: allocated 3234kB for md0
[36639.588294] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[36639.588296] RAID5 conf printout:
[36639.588297]  --- rd:3 wd:3
[36639.588298]  disk 0, o:1, dev:sdb
[36639.588300]  disk 1, o:1, dev:sdc
[36639.588301]  disk 2, o:1, dev:sde
[36647.098007] VFS: Can't find ext3 filesystem on dev md0.
[37087.756191] VFS: Can't find ext3 filesystem on dev md0.
```

---

### Post by fjgaude on 2009-02-10
With your new install did you create a mountpoint for the array?

---

### Post by Kilbasar on 2009-02-10
No, the only mountpoints I made were for "/",  and my windows partition. I later created "/raid" with the intention of mounting my raid5 there. I did a manual partitioning during the install, and all I partitioned/formatted was my "/" partition. It should not have touched my raid5 disks in any way. Based on the fact that mdadm still reports the correct array creation date, size, and space used, and that I have not run "mdadm --create", I am confident that my data is still there. But I can't figure out why it doesn't show up as an ext3 partition, and why I am unable to mount it. Thanks!

---

### Post by fjgaude on 2009-02-10
Make a mountpoint now:

```
sudo mkdir /home/raid
```

Then do this:

```
sudo mount /dev/md0 /home/raid
```

Of course you can use any name you wish instead of /raid, and have it on other than /home.

---

### Post by Kilbasar on 2009-02-10
Hi. Thanks, but unfortunately, I don't think you understand my problem. I cannot mount, because the system does not see the ext3 partition on the raid5 array:

```
# sudo mkdir /home/raid
# sudo mount /dev/md0 /home/raid
mount: you must specify the filesystem type
# sudo mount -t ext3 /dev/md0 /home/raid
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
# dmesg|tail -1
[118517.394256] VFS: Can't find ext3 filesystem on dev md0.
# sudo fdisk -l /dev/md0

Disk /dev/md0: 1500.3 GB, 1500312502272 bytes
255 heads, 63 sectors/track, 182402 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009860b

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       91201   732572001   fd  Linux raid autodetect
```

As I mentioned earlier, mdadm seems to have all the correct parameters for my raid5, and shows the correct creation date etc. However, it does not see the ext3 partition that I know is there. I have not touched the raid5 in any way since my re-install, prior to which it was working perfectly.

Any mdadm experts out there who can lend a hand? Thanks!

---

### Post by fjgaude on 2009-02-11
Look, **fdisk** doesn't understand raid arrays.

What is the mountpoint created for your array?

---

### Post by Kilbasar on 2009-02-11
Hi. Thanks for your help. The mount point should not matter. I can try mounting it at /raid, /home/raid, or wherever else; the system does not see that there is an ext3 partition on the array, so it refuses to mount:

```
# sudo mkdir /mnt/raid
# sudo mount -t ext3 /dev/md0 /mnt/raid
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
# dmesg | tail -1
[198545.851876] VFS: Can't find ext3 filesystem on dev md0.
```

Thanks agin.

---

### Post by fjgaude on 2009-02-11
Well, I guess somekind of corruption has caused the filesystem to appear not there... I have no thought other than to install ext3... but I'm sure that will cause all data to be lost.

Unless you don't have ext3 on the array... and you did create a mountpoint using **mkdir**?

---

### Post by Kilbasar on 2009-02-11
This array had a pre-existing ext3 partition. The data is still there, but it is not showing up as such. I have a hunch there is an "mdadm --create" command that could fix this (by re-creating the array using the pre-existing data), but I only get one shot at it, because an incorrect "mdadm --create" would permanently destroy the data. 

My only theory for why the array isn't working is that maybe when I originally created it I used some setting (chunk size?) that was not auto-detected when mdadm re-assembled it. But all this should be in the superblock. Maybe the UUIDs of the drives changes, and that's causing the issue somehow?

Are there any mdadm experts out there who might have any ideas? I really appreciate it.

---

