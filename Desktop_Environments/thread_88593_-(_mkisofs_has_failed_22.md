---
title: ":-( mkisofs has failed: 22"
date: 2005-11-10
forum: Desktop Environments
---

### Post by nene on 2005-11-10
hi, when i try to write a multisession DVD with k3b, I have this error:

:-( mkisofs has failed: 22

i check to debugging output and I find this:

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
DVDRW USB 16X A089 (/dev/scd0, /dev/sg0) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

HL-DT-ST RW/DVD GCC-4241N 0C27 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]
Used versions
-----------------------
growisofs: 5.21
mkisofs: 2.1-unofficial-iconv

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
/usr/bin/mkisofs: Invalid argument. Seek error on old image
:-( mkisofs has failed: 22

growisofs command:
-----------------------
/usr/bin/growisofs -M /dev/scd0 -use-the-force-luke=notray -use-the-force-luke=tty -speed=6 -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-nene/k3bbprxBb.tmp -rational-rock -hide-list /tmp/kde-nene/k3bDn8C8b.tmp -joliet -hide-joliet-list /tmp/kde-nene/k3bwyXhgb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-nene/k3bnjbhSa.tmp 


where is the matter??
th

---

