---
title: "hard drives"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Derek14021966 on 2006-01-05
Hi I need help, (obviously), have installed Ubuntu 5.10, works generally well, but i have to manually mount my second hard drive to be able to use it. is there a way to make it auto mount. The drive in question is a secondary master on the 2nd ide cable, my os is on the primary master, and my cdrom/dvdrom's are primary/secondary slaves. i have included the mseg listing,

hda: SAMSUNG SV1021D, ATA DISK drive
hdb: CD-ROM CCD-52X6S, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hdc: ST320413A, ATA DISK drive
hdd: LITE-ON DVDRW SOHW-1673S, ATAPI CD/DVD-ROM drive


and my partitions are

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 2330 18715693+ 83 Linux
/dev/hdc2 2331 2434 835380 5 Extended
/dev/hdc5 2331 2434 835348+ 82 Linux swap / Solaris

and my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

Thanks

---

### Post by syklitengutt on 2006-01-05
[http://ubuntuguide.org]("http://ubuntuguide.org")
You find your answer there---

---

### Post by jonathanm on 2006-01-05
this is confusing, has your fstab been set up by ubuntu?

fdisk is saying that your /dev/hdc drive (secondary master) contains your boot (*) and swap in which case /dev/hda should have your root (/) on it.

This is not the case in fstab though as it has been set up with no boot and a swap partition on /dev/hda5 instead of on /dev/hdc5 as fdisk says

---

