---
title: "cd-r rw writing error in ubuntu"
date: 2006-08-13
forum: Desktop Environments
---

### Post by ales on 2006-08-13
hello I have problem with the cd/dvd creator and also gnomebaker etc. always after writing a short time I get error message. See below. Has anyone same problem? Is there somewhere a clue how to solve it?




cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A301'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 17771 kB/s 100x CD 12x DVD
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
Starting new track at sector: 0
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 03 46 17 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 10 56 B6 ED 80 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.016s timeout 200s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 439400448 bytes
Writing  time:  152.825s
Average write speed  21.9x.
Min drive buffer fill was 97%
Fixating...
Fixating time:    7.511s
cdrecord: fifo had 6985 puts and 6922 gets.
cdrecord: fifo was 0 times empty and 5160 times full, min fill was 85%.

---

### Post by savethesavior on 2006-08-16
I'm having a similar problem with my Iomega zip CD 650 USB burner. When trying to write an audio cd, it converts the tracks, then starts to burn them onto the disc, after a few moments it give me an error that just says "Error writing cd." There's no problems reading from the drive, just writing to it. It worked fine while using windows, so I don't think the drive itself is malfunctioning. 

I'll find the error number when I get home and post it tonight. 

It's frusturating because it's the only thing that hasn't worked since I switched to Ubuntu. Everything else has been fantastic.

---

### Post by PhilJ on 2006-08-16
try setting cdrecord as suid root

using command

sudo dpkg-reconfigure cdrecord

then add

chown root: cdrom /dev/whatever your device is listed as ( eg hdd sdo etc from  /etc/fstab ) 

to   /etc/rc.local (you have to be root to amend file)

the details are in another thread .. cd burning issues 

philj


g

---

