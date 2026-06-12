---
title: "dvd:rip CD Burning problem"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Sale on 2006-10-04
Hi

I've installed dvd::rip with Automatix (Dapper)

Under Cd Burning tag in Global Prefferences, I get the following error message:

cdrecord device (n,n,n or filename): [COLOR="Red"]0,X,0 has not format n,n,n and is no file: NOT Ok[/COLOR]

What does this mean, and, how do I resolve this problem?

---

### Post by tatimmer on 2006-10-04
I have a script on my website for burning a datacd that uses cdrecord.


I ran <cdrecord -scanbus> to get the "dev=ATA:1,1,0" string for my drive

---

### Post by Sale on 2006-10-05
cdrecord -scanbus only lists my two SATA hard drives...

On the other hand, here is an output from cdrecord -checkdrive with a higlited part that I think is a problem:

sale@sale-at-home:~$ cdrecord -checkdrive
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-110D'
Revision       : '1.39'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
[COLOR="Red"]cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.[/COLOR]
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

---

