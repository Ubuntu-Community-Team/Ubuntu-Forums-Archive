---
title: "Move/shrink NTFS boot partition problem"
date: 2009-03-27
forum: General Help
---

### Post by Dark Neutron on 2009-03-27
I just got a 1TB hard drive to replace my current pair of 500GB drives, which I plan to use as backup drives. I currently have Windows XP on one drive and Ubuntu 8.10 on the other. My goal is to move both OS's and one data partition to the larger drive. In doing so, I want to shrink the windows partition by 8 GiB. Let me try to be as clear as I can about what I tried and what went wrong.

Original partition setup (partition id's from GParted):

Windows XP NTFS, 40GiB on /dev/sda1 (C:)
Data NTFS, 425.76 GiB on /dev/sda2 (D:)
Data2 NTFS, 439.45 GiB on /dev/sdb1(E:)

Inside an extended partition of 23.61GiB on /dev/sdb3:
Ubuntu root ext3, 11.08 GiB on /dev/sdb
unallocated 4.89 MiB
linux-swap, 3.85 Gib on /dev/sdb5
Ubuntu /home ext3, 11.37 GiB on /dev/sdb6

First attempt:
I used GParted to move  /dev/sda1 to /dev/sdc1 and shrink it from 40 GiB to 32 GiB, and move /dev/sda2 to /dev/sdc2.  I then created an extended partition at the end of the drive and copied all the Linux partitions to there. Then /dev/sdc2 was expanded to ~870 GiB, filling the rest of the unallocated space at the center of the drive. Finally, I told GRUB to look for Ubuntu on hd0,4 and disconnected the two 500GiB drives for safety and to reduce confusion.

First problem:
Linux booted fine, but trying to boot Windows caused the system to hang at GRUBs "Starting  up..." message.

First attempted fix:
I booted into the windows recovery console and tired the following commands: fixboot, bootcfg /rebuild, fixmbr.  I then reinstalled GRUB. Even doing fixmbr and leaving GRUB out of the picture did not help. It just said no boot disk found (or an error to that extent). I then erased the 1TiB drive and tried the entire process over again, with no better success.

Second attempt (more successful):
I used this command to copy over the data:
```
dd if=/dev/sda of=/dev/sdb bs=32256
```
then used GParted to copy the Ubuntu partitions to the end of the drive. This worked, in that both windows an Ubuntu booted correctly.

Second problem:
This occured when I tried to resize /dev/sdc1 from 40 GiB to 32 GiB. The partition only had ~27 GiB of data on it (and it was defragmented with DirMS), so I thought it should have worked correctly. I also moved /dev/sdc2 to fill in the new gap on the drive. Alas, this caused the same problem as described above. None of the above fixes were any more successful.

Some thoughts:
As best as I can tell, it looks like ntfsresize (that GParted uses) is damaging the windows bootloader when it is copied to /dev/sdc1 or modifies that partition in any way. The rest of the data appears to have been copied fine, as I can open files and such, so I am assuming that windows itself is still intact and it is just the bootloader that is broken. On the other hand, I thought the fixboot command from the windows recovery console should have rewritten the windows bootloader. Thus I am left sightly uncertain as to where the actual problem lies.

So, after my somewhat long and convoluted description, I am asking for help here. First of all, what is actually going on here? And second, is there a different way for me to accomplish what I want that I have not discovered yet?

I like to think myself as good at working on computers (I am currently going for a bachelors degree in computer science), but there is always something to show me how little I really know...

Additional partition data (current):
results of "sudo parted --list"
```
odel: ATA WDC WD5000KS-00M (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  42.9GB  42.9GB  primary  ntfs         boot 
 2      42.9GB  500GB   457GB   primary  ntfs              


Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  472GB  472GB   primary   ntfs         boot 
 3      472GB   500GB  28.2GB  extended               lba  
 7      472GB   484GB  11.9GB  logical   ext3              
 5      484GB   488GB  4135MB  logical   linux-swap        
 6      488GB   500GB  12.2GB  logical   ext3              


Model: ATA WDC WD10EADS-00L (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

```

results of "fdisk -l"
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0dd56d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       83220    41942848+   7  HPFS/NTFS
/dev/sda2           83221      969018   446442192    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xfe740fdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      914286   460800112+   7  HPFS/NTFS
/dev/sdb3          914287      969021    27586126    f  W95 Ext'd (LBA)
/dev/sdb5          937359      945371     4038520+  82  Linux swap / Solaris
/dev/sdb6          945372      969021    11919568+  83  Linux
/dev/sdb7          914287      937349    11622996   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2d77f30

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by dcstar on 2009-03-28
> **Dark Neutron said:**
> 
.......
First attempt:
I used GParted to move  /dev/sda1 to /dev/sdc1 and shrink it from 40 GiB to 32 GiB, and move /dev/sda2 to /dev/sdc2.  I then created an extended partition at the end of the drive and copied all the Linux partitions to there. Then /dev/sdc2 was expanded to ~870 GiB, filling the rest of the unallocated space at the center of the drive. Finally, I told GRUB to look for Ubuntu on hd0,4 and disconnected the two 500GiB drives for safety and to reduce confusion.

First problem:
Linux booted fine, but trying to boot Windows caused the system to hang at GRUBs "Starting  up..." message.

First attempted fix:
I booted into the windows recovery console and tired the following commands: fixboot, bootcfg /rebuild, fixmbr.  I then reinstalled GRUB. Even doing fixmbr and leaving GRUB out of the picture did not help. It just said no boot disk found (or an error to that extent). I then erased the 1TiB drive and tried the entire process over again, with no better success.

Second attempt (more successful):
I used this command to copy over the data:
```
dd if=/dev/sda of=/dev/sdb bs=32256
```
then used GParted to copy the Ubuntu partitions to the end of the drive. This worked, in that both windows an Ubuntu booted correctly.

Second problem:
This occured when I tried to resize /dev/sdc1 from 40 GiB to 32 GiB. The partition only had ~27 GiB of data on it (and it was defragmented with DirMS), so I thought it should have worked correctly. I also moved /dev/sdc2 to fill in the new gap on the drive. Alas, this caused the same problem as described above. None of the above fixes were any more successful.

Some thoughts:
As best as I can tell, it looks like ntfsresize (that GParted uses) is damaging the windows bootloader when it is copied to /dev/sdc1 or modifies that partition in any way. The rest of the data appears to have been copied fine, as I can open files and such, so I am assuming that windows itself is still intact and it is just the bootloader that is broken. On the other hand, I thought the fixboot command from the windows recovery console should have rewritten the windows bootloader. Thus I am left sightly uncertain as to where the actual problem lies.
.......

If you want to boot things like Windows partitions then you have to manually change things on the /boot/grub/menu.lst file to allow for the new drives/partitions you are trying to use. The Windows "root" data is particularly important.

When you have multiple drive you have to be fully aware of which one is actually booting.

---

### Post by Dark Neutron on 2009-03-28
As I mentioned, windows booted correctly after using the dd command to do the copying. The problems only started after the partition was resized. That seems to imply to me that GRUB is not the cause of my problems.  Somehow, ntfsresize seems to be damaging the volume boot record on /dev/sdc1 without damaging any other files.

I should also mention that when I was booting off the new drive, I had the other two physically unplugged so that I would not have to worry about multiple drive conflicts.

---

