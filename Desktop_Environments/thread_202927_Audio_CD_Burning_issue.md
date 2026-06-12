---
title: "Audio CD Burning issue"
date: 2006-06-24
forum: Desktop Environments
---

### Post by p0liX on 2006-06-24
After upgrading to 6.06, I'm unable to burn audio cds.  I can burn data just fine.  I've tried using Serpentine and Gnomebaker and both fail.  

Here is the output from Gnomebaker...

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-25-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX830E  '
Revision       : 'JPK4'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1895168 = 1850 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
cdrecord: No such file or directory. Cannot open '/tmp/GnomeBaker/p0lix/create_audiocd/gbtrack_12.wav'.

```

It converts the mp3's fine, but fails when it begins to burn.  I looked at /tmp/GnomeBaker/p0lix/create_audiocd/gbtrack_12.wav and the file is there and has the proper permissions, so i'm not sure why it says "no such file"

Any idea how to remedy this?

---

