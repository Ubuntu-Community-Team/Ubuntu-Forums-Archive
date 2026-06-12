---
title: "Disks Manager Partition info incorrect"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Ginger The Cat on 2006-01-01
My Disks Manager Partition info is not correct. By that I mean it doesn't match the output I get from doing a df for example


I've changed so many things that I can't remember clearly enough to give a proper explanation of what I did and when but it went something like this...


I setup a dual boot Breezy + XP on my Inspiron 6000 laptop by using bootpart and grub.

It was all working fine so I decided to try out Dapper and created another partition for it, installed it ok and it was also working ok and I could successfully choose between XP, Breezy and Dapper.

Then for some unknown reason on boot the screen stuck at a GRUB promt. I found a solution from someone with the same problem, something about windows and linux compatibility problem. The solution being this command

sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda

This solved my problem. I then decided Dapper wasn't for me so erased it and decided to use the partition as a /home for my Breezy which was until then all in one partition.

This went wrong and I couldnt log in as /home had gone missing. In trying to sort it out I temporarily called it /home1 which is what it is at the moment

So now I have the following...


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        1313    10450282+   7  HPFS/NTFS
/dev/sda3            2610        6903    34491555    f  W95 Ext'd (LBA)
/dev/sda4            6904        7295     3148740   db  CP/M / CTOS / ...
/dev/sda5            2610        3884    10241406    b  W95 FAT32
/dev/sda6            3885        5562    13478503+  83  Linux
/dev/sda7            6777        6903     1020096   82  Linux swap / Solaris
/dev/sda8            5563        6776     9751423+  83  Linux

sda2 is my Windows XP C drive
sda 1 and 4 are some laptop diag partitions etc
sda 5 is a data drive on my Windows system that I access on Windows and Ubuntu
sda6 is my root and sda8 my intended future /home

My fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8       /home           ext3    defaults        0       2
# /dev/sda1       /media/sda1     vfat    defaults        0       0
# /dev/sda2       /media/sda2     ntfs    defaults        0       0
# /dev/sda4       /media/sda4     vfat    defaults        0       0
/dev/sda5       /DriveG     vfat    auto,user,rw,umask=000        0       0
/dev/sda7       none            swap    sw              0       0
/dev/sda8	/home1	ext3	auto,user,rw	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


This all works fine except for one puzzling effect. When I run the Disks Admin program on the Partitions Tab it shows

Partition 1       /dev/sda1
Partition 2       /dev/sda2
Partition 5       /dev/sda5 Access Path /DriveG
Partition 6       /dev/sda6  Access Path /home1
Swap Partition /dev/sda7
Partition 4        /dev/sda4


 /dev/sda6 is set to /home1 instead of /dev/sda8 which doesn't make sense as /dev/sda6 is where the filesystem root is.

If I click Disable in the Disk Manager the display changes to the correct /dev/sda6 mapped to / but coming out and going back in shows it back again to its incorrect setting. Running sudo disks-admin from a terminal lets me see a hidden error message of :11248 Warning umount: /: device is busy repeated twice.

I'm now nervous about changing anything in case I break it (in a more serious way)

Any ideas? I can't find much info on disks-admin either. Where and how does it get its information. Is there any way of resetting it?

Cheers

Mike

---

