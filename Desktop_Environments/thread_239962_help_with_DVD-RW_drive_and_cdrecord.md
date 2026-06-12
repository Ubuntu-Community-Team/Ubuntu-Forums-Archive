---
title: "help with DVD-RW drive and cdrecord"
date: 2006-08-20
forum: Desktop Environments
---

### Post by scifan on 2006-08-20
I've searched, and tried a couple of things, and have a bit of a puzzle here.


I have 2 computers at home (notebook & desktop) that are running dapper...

The notebook is an Acer 5672 and it's autodetecting it's Matshita DVD burner and automatically configuring it as a scsi emulated drive.  I can burn to it, and everything seems to work fine.

The desktop box is used as my media pc.  (ATI x200 chipset, Sony DW-Q30A burner, has a pata 200gb drive and a sata 160gb drive).  This box only seems to detect the Sony dvd rw drive as /dev/hdc.

When I try to write an ISO to a DVD-R blank, I get: 
> 
root@mediapc:/isolocation# cdrecord-wrapper.sh valid.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'SONY    '
Identifikation : 'DVD RW DW-Q30A  '
Revision       : 'YYS3'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD/DVD driver (checks media) (mmc_cd_dvd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
cdrecord: Unspecified command not implemented for this drive.
cdrecord: Data will not fit on any disk.
cdrecord: Cannot write more than remaining DVD capacity.



Note that the file is ~ 3.1 gb, and the media is a brand new fuji 4.7gb disk...

I notice that the drive on the notebook is associated with scd0 while the drive on the desktop is associated with hdc.

Something else that's whacked is when I issue a -scanbus command to cdrecord, I get the sata bus w/ the 160gb drive listed... 

Any idea's?

---

### Post by scifan on 2006-08-27
I guess that no one has any suggestions on this...

---

### Post by Omnios on 2006-08-27
Basicly I used **Automatix to install my cd stuff and CDRW/DVDRW and it just worked. YOu might want to give it a try**
[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

