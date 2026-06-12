---
title: "Strange problem with burrning CDs"
date: 2006-02-21
forum: Desktop Environments
---

### Post by tomcio on 2006-02-21
Hi!

A few days ago i changed my computer and now I can't burn CD, ut I can burn DVDs and normally mount CD/DVD with data?! When I insert empty CD disc into my DVD-RW, I only get this:
[INDENT][SIZE=1]
[I]mount: I could not determine the filesystem type, and none was specified
[/I] [/SIZE][/INDENT]

tis is my **fstab**:
[I][INDENT][SIZE="1"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    iocharset=utf8,umask=000       0       0/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto    user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/SIZE][/INDENT][/I]

and K3B debug output:
[I][SIZE="1"][INDENT]System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-686
Devices
-----------------------
LITE-ON DVDRW SOHW-1693S KS02 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R dwuwarstwowa; DVD+R; DVD+RW; DVD+R dwuwarstwowa] [DVD-ROM; DVD-R sekwencyjna; DVD-R dwuwarstwowa sekwencyjna; DVD-RW w trybie ograniczonego zast&#281;powania; DVD-RW sekwencyjny; DVD+RW; DVD+R; DVD+R dwuwarstwowa; CD-ROM; CD-R; CD-RW] [Sesja naraz (SAO); TAO; RAW; SAO/R96P; SAO/R96R; Surowe/R16; Surowe/R96P; Surowe/R96R; Ograniczone zast&#281;powanie]

K3b
-----------------------
Size of filesystem calculated: 4822

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
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
TOC Type: 3 = CD-ROM XA mode 2

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=6 -tao driveropts=burnfree -eject -multi -xa -tsize=4822s - 

mkisofs
-----------------------
4822
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-tomek/k3bLvYThb.tmp -rational-rock -hide-list /tmp/kde-tomek/k3bZh4Qma.tmp -joliet -hide-joliet-list /tmp/kde-tomek/k3bMbTZjc.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-tomek/k3bs5C8ob.tmp [/INDENT][/SIZE][/I]

I didn't changed my DVD burner and it worked fine on my old maschine..

Any ideas how to fix it?

---

