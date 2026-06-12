---
title: "K3b Error"
date: 2006-01-17
forum: Desktop Environments
---

### Post by rado_london on 2006-01-17
Hi 
I just wanted to erase a CD-RW when I got the following message:
```
System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
TSSTcorp CD/DVDW TS-L532R HA04 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=10 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdb'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM

```

Help me please

Thank you

---

### Post by qferret on 2006-01-17
equivalent of trying to format a mounted partition?

un-mount /media/cdrom0 and try it once

---

### Post by rado_london on 2006-01-18
Thanks a lot.
However after a reboot it worked!

---

### Post by vampaz on 2006-01-24
hello,

i'm also having the same problem, and this solution doesn't work for me.Maybee it's simple but i'm very very new to all this...

---

