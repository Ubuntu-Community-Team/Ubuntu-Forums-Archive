---
title: "Problems burning with cdrecord"
date: 2005-01-19
forum: Desktop Environments
---

### Post by lerio on 2005-01-19
Hi,

i used to burn with no problems until a week ago. then i tried to burn an audio cd on a rewritable cd with cdrecord. the burn process was fine (no error messages), but effectively no data was written. i tried several other options in cdrecord with no luck. so i decided to reinstall winxp home and try to burn again other files on different cd-types but i wasn't still able to burn or erase those discs. xp was basically unable to see blank discs inserted in the drive (but i've always been able to read any other type of cd). i went in the bios and i reverted the options to its default values. after that, blank discs were detected successfully and burn process went fine. but! after cheching the disc no data was written onto it!!!! so it seemed that on xp i had the same issues than on ubuntu. so i reinstalled ubuntu again (warty) with kernel 2.6.8.1-4-686, and every time i try to burn, erase or even msinfo with cdrecord i get the following messages, example:

-----------------------------------------------------------------

sudo cdrecord -v dev=/dev/hdc -msinfo

Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'QSI     '
Identifikation : 'DVD/CDRW SBW-161'
Revision       : 'SU03'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x0010
Profile: 0x0008
Profile: 0x0009 (current)
Profile: 0x000A
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1605632 = 1568 KB
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
cdrecord: Success. read toc: scsi sendcmd: no error
CDB:  43 00 01 00 00 00 00 00 04 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 4
cmd finished after 0.000s timeout 40s
cdrecord: Cannot read session offset

-----------------------------------------------------------------

PLEASE, help me.

ps: ah, my cd writer is a QSI SBW-161 (combo: dvd reader and cdrw) on a gericom athlon xp 1400 laptop

thanks a lot

---

### Post by lerio on 2005-01-19
any kind of suggestion/check/test to perform/idea is really welcome....
I don't wanna trash my cd burner yet!

---

### Post by lerio on 2005-01-22
as suggested in the #ubuntu channel, i tried to clean the lens with a cleaning tool, but the result is the same. if you have something to say please do it!

---

### Post by Narcelio Filho on 2006-03-12
I had the same problem, but while trying to burn a DVD-RW. It just worked when I used [growisofs]("http://fy.chalmers.se/~appro/linux/DVD+RW").

---

