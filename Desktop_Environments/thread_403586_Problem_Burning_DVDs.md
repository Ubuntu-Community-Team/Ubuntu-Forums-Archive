---
title: "Problem Burning DVDs"
date: 2007-04-07
forum: Desktop Environments
---

### Post by roytang on 2007-04-07
Hi,

I'm using k3b in Edgy to burn DVDs (data discs). A few weeks ago I was able to burn a few generic discs without any problem. This weekend I had some problems burning to both DVD+R and DVD-R discs. Yesterday I was able to burn only 2 out of 4 discs successfully. Today I already wasted 3 discs trying out various write speeds, settings, etc. K3b debug log shows the ff:
=======================================
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
LITE-ON DVDRW SOHW-1693S KS0A (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

K3b
-----------------------
Size of filesystem calculated: 2256085

Used versions
-----------------------
growisofs: 6.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 8.2x1385KBps.
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
         0/4620462080 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
:-( unable to WRITE@LBA=0h: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hda=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2256085 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2256085
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.02% done, estimate finish Sun Apr  8 03:58:28 2007
  0.04% done, estimate finish Sun Apr  8 00:21:39 2007
  0.07% done, estimate finish Sat Apr  7 23:32:50 2007
  0.09% done, estimate finish Sat Apr  7 23:08:14 2007
  0.11% done, estimate finish Sat Apr  7 22:37:34 2007
  0.13% done, estimate finish Sat Apr  7 22:30:20 2007
  0.16% done, estimate finish Sat Apr  7 22:14:24 2007
  0.18% done, estimate finish Sat Apr  7 22:11:50 2007
  0.20% done, estimate finish Sat Apr  7 22:01:10 2007
  0.22% done, estimate finish Sat Apr  7 21:52:54 2007
  0.24% done, estimate finish Sat Apr  7 21:52:58 2007
  0.27% done, estimate finish Sat Apr  7 21:46:46 2007
  0.29% done, estimate finish Sat Apr  7 21:47:07 2007
  0.31% done, estimate finish Sat Apr  7 21:42:13 2007
  0.33% done, estimate finish Sat Apr  7 21:37:57 2007
  0.35% done, estimate finish Sat Apr  7 21:38:56 2007
  0.38% done, estimate finish Sat Apr  7 21:39:40 2007
  0.40% done, estimate finish Sat Apr  7 21:36:16 2007
  0.42% done, estimate finish Sat Apr  7 21:33:13 2007
  0.44% done, estimate finish Sat Apr  7 21:34:14 2007
  0.47% done, estimate finish Sat Apr  7 21:35:03 2007
  0.49% done, estimate finish Sat Apr  7 21:32:29 2007
  0.51% done, estimate finish Sat Apr  7 21:30:07 2007
  0.53% done, estimate finish Sat Apr  7 21:27:58 2007
  0.55% done, estimate finish Sat Apr  7 21:28:55 2007
  0.58% done, estimate finish Sat Apr  7 21:26:58 2007
  0.60% done, estimate finish Sat Apr  7 21:25:10 2007
  0.62% done, estimate finish Sat Apr  7 21:26:10 2007
  0.64% done, estimate finish Sat Apr  7 21:24:28 2007
  0.67% done, estimate finish Sat Apr  7 21:22:55 2007
  0.69% done, estimate finish Sat Apr  7 21:23:54 2007
  0.71% done, estimate finish Sat Apr  7 21:22:29 2007

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid OnePiece187-205 -volset  -appid  -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-roy/k3bU9B4Tb.tmp -rational-rock -hide-list /tmp/kde-roy/k3be6kE3b.tmp -joliet -hide-joliet-list /tmp/kde-roy/k3b8krZ0b.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-roy/k3bWPmfBb.tmp 

=======================================

I've found some bugs on launchpad that look similar:
[https://launchpad.net/ubuntu/+source/cdrtools/+bug/15424](https://launchpad.net/ubuntu/+source/cdrtools/+bug/15424)
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/91210](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/91210)
but neither of the above links have any solution. I assume that means they're not yet fixed?

Aside from waiting for one of the above issues to be resolved, is there anything I can check to diagnose the problem? I'm not sure if there's any difference between my system now and the last time I was able to burn discs successfully.

Any suggestions are most welcome. Thanks :)

---

