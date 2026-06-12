---
title: "CD Burn Error in 5.10 + k3b."
date: 2005-10-22
forum: Desktop Environments
---

### Post by subscrive on 2005-10-22
Hi All,

While trying to burn the files in ubuntu 5.10 + k3b, I am getting following error. Can anyone please help?

I used both k3b and sudo k3b.

"System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
SONY CD-RW  CRX230E QYS1 (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 283602

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX230E  '
Revision       : 'QYS1'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1422080 = 1388 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Trying to use high speed medium on low speed writer.
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 1 times full, min fill was 0%.
Track 01: data   553 MB        
Total size:      636 MB (63:01.38) = 283604 sectors
Lout start:      636 MB (63:03/29) = 283604 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 2
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -12374 (97:17/01)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  2 2T speed high: 10
  power mult factor: 2 6
  recommended erase/write power: 5
  A1 values: 24 2C DC
  A2 values: 14 A4 4A
  A3 values: 02 D2 80
Disk type:    Phase change
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 76245
Forcespeed is OFF.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hda speed=52 -tao driveropts=burnfree -eject -multi -xa -tsize=283602s - 

mkisofs
-----------------------
283602
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.18% done, estimate finish Sat Oct 22 15:00:09 2005
  0.36% done, estimate finish Sat Oct 22 14:41:49 2005
  0.53% done, estimate finish Sat Oct 22 14:35:44 2005
  0.71% done, estimate finish Sat Oct 22 14:32:32 2005

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-amitg/k3bvAzoaa.tmp -rational-rock -hide-list /tmp/kde-amitg/k3bz8ENrc.tmp -joliet -hide-joliet-list /tmp/kde-amitg/k3brifzta.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-amitg/k3bVkhsgb.tmp "

~A.

---

### Post by goneskiing on 2005-10-29
for some k3b doesn't work, for others it works flawless.  My experience:
I had same error messages as subscrive

nautilus crwriting - does not work
k3b from menus - does not work
command line k3b - does not work
sudo k3b - does not work
gksudo k3b - Works !!  (thank you who finally suggested this -saved me from lots of work switching)

sounds like some kind of permission issue

facts:  I installed Ubuntu from cd, then apt-get kbuntu-desktop via synaptics, kept gdm.  Like Subscrive, also have Sony CDRW (mine is combo CDRW, DVDR)

hope that helps.

---

### Post by subscrive on 2005-10-30
I can burn the cds using nautilus cd burner, k3b etc, if the cd is brand new blank read only cd.

but if I hv rewritable cd, which I hv already used in windows 98 using nero, then the cd burn fails.
Even after i erase the cd from nero and then try to burn the cd in linux, the cd burn fails.

Does anyone know how to go about this problem?

~A.

---

### Post by jvictor on 2005-10-30
For me GnomeBaker dint work at all, K3B worked partiallly, try GraveMan it works perfectly for me...(Sony DVD+RW RDRU810-A) I had to enable DMA.. that was another pain point .. :)

---

