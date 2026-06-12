---
title: "Auto mounting hard drives"
date: 2005-12-30
forum: General Help
---

### Post by Derek14021966 on 2005-12-30
Hi I need help, (obviously), have installed Ubuntu 5.10, works generally well, but i have to manually mount my second hard drive to be able to use it. is there a way to make it auto mount. The drive in question is a secondary master on the 2nd ide cable, my os is on the primary master, and my cdrom/dvdrom's are primary/secondary slaves. i have included the mseg listing, 

hda: SAMSUNG SV1021D, ATA DISK drive
hdb: CD-ROM CCD-52X6S, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hdc: ST320413A, ATA DISK drive
hdd: LITE-ON DVDRW SOHW-1673S, ATAPI CD/DVD-ROM drive

and my fstab file 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

I tried to edit the fstab file before, but unfortunatley i locked the system and wasn't able to get back in to fix the problem, (did you guess i was a newbie??) so i'm a bit wary about "just editing the fstab" again and would like some help so i don't have to reload everything again. Thanks, Derek

---

### Post by SickTwist on 2005-12-30
How is the second HDD partitioned? What filesystem(s) are in use on it? Run this command to list the partitions if you are not sure:

sudo fdisk -l /dev/hdc

---

### Post by Derek14021966 on 2005-12-30
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2330    18715693+  83  Linux
/dev/hdc2            2331        2434      835380    5  Extended
/dev/hdc5            2331        2434      835348+  82  Linux swap / Solaris

this is the output regarding my hard drives, thanks

---

