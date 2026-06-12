---
title: "Serious issues with cdrecord"
date: 2006-07-31
forum: Desktop Environments
---

### Post by sutterp on 2006-07-31
My Situation: (rant on)
I am currently evaluating ubuntu as a replacement for SuSE Linux on 12 workstations. I expect basic software to work 'out of the box', SuSE Linux doesn't give me this, so maybe I will be better off in making the switch.

I have ubuntu installed on two machines now, and I can't get cdrecord working. 

There are several threads in regard to cdrecord in this forum. Not one of the threads give a final answer/solution, so I assume I am not the only one who still has problems with cdrecord. First impression: With what I have seen, I'm doubtful whether to proceed.
(rant now off, sorry).

The problem:
cdrecord -scanbus returns an error. So I installed scsi support for the cd recorder.  cdrecord -scanbus now reports correctly:
> root@james:~# cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
<snip>Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'HL-DT-ST' 'CD-RW GCE-8526B ' '1.03' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *


I can now erase eraseable CD's, cdrecord -atip reports correctly

> root@james:~# cdrecord -atip dev=0,0,0
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
<snip>
cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 2
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identifikation : 'CD-RW GCE-8526B '
Revision       : '1.03'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11078 (97:34/22)
  ATIP start of lead out: 336075 (74:43/00)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation


Virtually all functions of cdrecord work now, except the actual burning process. This is what I get when running cdrecord from the command line.

> root@james:~# cdrecord -dev=0,0,0 -speed=24 -data -dao -v /bca/backup/Backup-to-cd-2006-07-30.iso
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/ 17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type : Removable CD-ROM
Version : 2
Response Format: 2
Capabilities :
Vendor_info : 'HL-DT-ST'
Identifikation : 'CD-RW GCE-8526B '
Revision : '1.03'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009
Profile: 0x0008
Profile: 0x0002 (current)
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1951488 = 1905 KB
FIFO size : 4194304 = 4096 KB
Track 01: data 73 MB
Total size: 84 MB (08:21.65) = 37624 sectors
Lout start: 84 MB (08:23/49) = 37624 sectors
Current Secsize: 2048
ATIP info from disk:
Indicated writing power: 6
Reference speed: 2
Is not unrestricted
Is erasable
ATIP start of lead in: -11078 (97:34/22)
ATIP start of lead out: 336075 (74:43/00)
1T speed low: 0 (reserved val 0) 1T speed high: 4
2T speed low: 0 (reserved val 5) 2T speed high: 0 (reserved val 12)
power mult factor: 3 5
recommended erase/write power: 3
A1 values: 02 3A B0
A2 values: 5C C6 26
Disk type: Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Trying to clear drive status.
cdrecord: Drive needs to reload the media to return to proper status.
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
cdrecord: Input/output error. send_cue_sheet: scsi sendcmd: no error
CDB: 5D 00 00 00 00 00 00 00 20 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 200s
cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
cdrecord: Cannot send CUE sheet.
cdrecord: Could not write Lead-in.
Writing time: 9.170s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

/var/log/messages reports
> ul 30 20:41:22 localhost kernel: [17180170.580000] end_request: I/O error, dev sr0, sector 0
Jul 30 20:42:31 localhost kernel: [17180236.628000] hdd: irq timeout: status=0xd0 { Busy }
Jul 30 20:42:31 localhost kernel: [17180236.628000] ide: failed opcode was: unknown
Jul 30 20:44:00 localhost kernel: [17180328.596000] hda: dma_timer_expiry: dma status == 0x21
Jul 30 20:44:41 localhost kernel: [17180338.596000] hda: DMA timeout error
Jul 30 20:44:41 localhost kernel: [17180338.596000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

The problem is not hardware related as the process works fine when booted into SuSE Linux on the same machine.

hdparm reports:

>  hdparm /dev/scd0

/dev/scd0:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

and 
> root@james:~# hdparm -i /dev/scd0

/dev/scd0:
 HDIO_GET_IDENTITY failed: Invalid argument


If I understand cd and dvd recorders correctly, they all understand scsi commands and cdrecord was written with this in mind. 

It appears that something is broken in the ubuntu version I am running:

root@james:~# uname -rs
Linux 2.6.15-26-386


I need some expert advise on how to fix this. 

Thanks for any hints and contributions.

Peter

---

### Post by steve4444 on 2006-08-28
that /var/log/messages log out put looks to indicate a issue a seek issue with the primary ide device. SATA and SCSI disks should show up as /dev/sd* so /dev/sda in the case of that lun id.

~Steve

---

