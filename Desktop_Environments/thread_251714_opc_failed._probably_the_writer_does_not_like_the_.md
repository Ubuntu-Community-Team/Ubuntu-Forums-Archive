---
title: "opc failed. probably the writer does not like the medium"
date: 2006-09-05
forum: Desktop Environments
---

### Post by pikakilla on 2006-09-05
Ive had this error for a couple of months. Ive searched google and the forums multiple times and havent found a solution. I am using 2.6.16-ck3 kernel with ubuntu 6.06. I do not know if this was an issue in 5.10 because i cannot remember if i burned any regular media. The odd part about this bug (more likely an error on my part) is that i can burn audio cd's, but i am unable to burn any form of a data cd. I have used many different kinds of cd's and many different cd's from the same and other spindles, so i dobut that it is a media issue. Debug output (pasting whole thing for those who may have this problem in the future so they can find it with search):

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.16-ck3
Devices
-----------------------
SAMSUNG CD-R/RW SW-248B R503 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R16; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.16-ck3
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SAMSUNG '
Identifikation : 'CD-R/RW SW-248B '
Revision       : 'R503'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 7300608 = 7129 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   441 MB        
Total size:      507 MB (50:13.97) = 226048 sectors
Lout start:      507 MB (50:15/73) = 226048 sectors
Current Secsize: 2048
  ATIP start of lead in:  -11231 (97:32/19)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 27
Manufacturer: Prodisc Technology Inc.
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 133798
Starting to write CD/DVD at speed 48 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
/usr/bin/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 13.495s timeout 200s
/usr/bin/cdrecord: OPC failed.
Writing  time:   18.160s
/usr/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=48 -dao driveropts=burnfree -eject -data /home/pikakilla/Desktop/KNOPPIX_V5.0.1CD-2006-06-01-DE.iso 

This is not unique to k3b and it pops its head in every burning program, but i am showing k3b's output because it gives the most detailed description of the problem. 

EDIT: [http://pastebin.ca/162145](http://pastebin.ca/162145)
(more errors to help clarify (tried it with sudo immediately after))

[http://pastebin.ca/162155](http://pastebin.ca/162155)
     ^===/var/log/messages

I checked to see if dma was enabled (checked all possible media locations /dev/hdb /media/cdrom0 (tried it out of desperation ](*,)) /dev/cdrom /dev/cdrw)

If any other information is needed, ill happily provide it. 
Thanks in advance,
Sam Adams

---

### Post by pikakilla on 2006-09-06
morning bump

---

### Post by pikakilla on 2006-09-06
bump (sorry for the bumps, but im completely stumped and my searching has proved no results)

---

### Post by pikakilla on 2006-09-07
trying one last time...

---

### Post by pikakilla on 2006-09-07
Fixed! Upon further research and the kind folks on the ubuntu irc server, the  culprit was discovered to be the lack of scsi emulation present.

---

### Post by foxxx on 2007-02-27
so what did you do to fix it??

---

### Post by pikakilla on 2007-04-29
To elaborate, i "fixed" it. It will burn music cds but wont burn data cd's. The problem is with the drive itself. The version of cdrecord that i had was not compatable with burning data cds. With the fork in the project, this might have changed, but i havent checked recently.

---

