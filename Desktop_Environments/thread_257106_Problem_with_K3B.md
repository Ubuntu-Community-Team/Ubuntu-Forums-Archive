---
title: "Problem with K3B"
date: 2006-09-14
forum: Desktop Environments
---

### Post by kill_u on 2006-09-14
Hi all
I’m a Ubuntu 6.06 user and have a problem with K3B software. The K3B don’t want to write DVD-RW disks. After trying to write he gives me this kind error:
```

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-23-386
Devices
-----------------------
_NEC DVD_RW ND-4550A 1.07 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

HL-DT-ST CD-RW GCE-8527B 1.02 (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]
Used versions
-----------------------
growisofs: 5.21
mkisofs: 2.1-unofficial-iconv

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
Rock Ridge signatures found
/usr/bin/X11/mkisofs: Error: '/rr_moved/content' and '/rr_moved/content' have the same Rock Ridge name 'content'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/content' and '/rr_moved/content' have the same Rock Ridge name 'content'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/content' and '/rr_moved/content' have the same Rock Ridge name 'content'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/content' and '/rr_moved/content' have the same Rock Ridge name 'content'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/content' and '/rr_moved/content' have the same Rock Ridge name 'content'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/content' and '/rr_moved/content' have the same Rock Ridge name 'content'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/binary-i386' and '/rr_moved/binary-i386' have the same Rock Ridge name 'binary-i386'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/binary-i386' and '/rr_moved/binary-i386' have the same Rock Ridge name 'binary-i386'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/binary-i386' and '/rr_moved/binary-i386' have the same Rock Ridge name 'binary-i386'.
/usr/bin/X11/mkisofs: Error: '/rr_moved/binary-i386' and '/rr_moved/binary-i386' have the same Rock Ridge name 'binary-i386'.
/usr/bin/X11/mkisofs: Unable to sort directory /rr_moved
:-( mkisofs has failed: 255

growisofs command:
-----------------------
/usr/bin/X11/growisofs -M /dev/hdc -use-the-force-luke=notray -use-the-force-luke=tty -speed=4 -gui -graft-points -volid Child movie -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher kill_u -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-mjekov/k3b5MfEgb.tmp -rational-rock -hide-list /tmp/kde-mjekov/k3bACA9xb.tmp -joliet -hide-joliet-list /tmp/kde-mjekov/k3bcLUQ3b.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-mjekov/k3bhDP9ec.tmp

```
These are the full log. Do you have any idea?
Gnome baker works without any problems.

---

