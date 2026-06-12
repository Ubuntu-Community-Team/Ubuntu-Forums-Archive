---
title: "CDrecorder"
date: 2005-04-07
forum: Desktop Environments
---

### Post by Jad on 2005-04-07
Salam shabab
shabab, I'm having troubles in burning data,  I have lose about 15 sony CD (you know what I mean $$) 
OS: Ubuntu Hoary
Device: Aopen 52x24x52x
I have tried k3b, nero, Nautilus, and gnome-baker. all giving same error.  

Here is one of the error messages by gnome-baker. 
```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'AOPEN   '
Identifikation : 'CD-RW CRW5224   '
Revision       : '1.05'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x0008 
Profile: 0x0009 (current)
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1359872 = 1328 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data   679 MB        
Total size:      780 MB (77:18.44) = 347883 sectors
Lout start:      780 MB (77:20/33) = 347883 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 11966
Forcespeed is OFF.
Starting to write CD/DVD at speed 12 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of  679 MB written.
Track 01:    1 of  679 MB written (fifo  96%) [buf  80%] 103.1x.
Track 01:    2 of  679 MB written (fifo 100%) [buf 100%]   6.3x.
Track 01:    3 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:    4 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:    5 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:    6 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:    7 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:    8 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:    9 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   10 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:   11 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   12 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   13 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   14 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   15 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   16 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   17 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   18 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   19 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   20 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   21 of  679 MB written (fifo 100%) [buf 100%]  12.5x.
Track 01:   22 of  679 MB written (fifo 100%) [buf 100%]  12.1x.
Track 01:   23 of  679 MB written (fifo  92%) [buf  91%]  11.3x.
Track 01:   24 of  679 MB written (fifo 100%)   4.7x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 30 13 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 30 15 0C 00 00 00 00 10 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x10 Qual 0x02 (id crc or ecc error) [No matching qualifier] Fru 0x0
Sense flags: Blk 12309 (valid) 
resid: 63488
cmd finished after 0.005s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 25204736 bytes
Writing  time:   30.309s
Average write speed 224.8x.
Min drive buffer fill was 91%
Fixating...
Fixating time:   21.907s
cdrecord: fifo had 461 puts and 398 gets.
cdrecord: fifo was 0 times empty and 364 times full, min fill was 87%.

``` 

please advise.

---

### Post by Juergen on 2005-04-07
Did you try burning as root? You might have to set the setuid bit.
What groups are you in?

BTW: to me it seems that the burning was successful, despite all this error messages. You tried to read your CDs, didn't you? :-)

Maybe you could try to get a RW until you have it working.

---

### Post by Jad on 2005-04-07
Why someone have to run any burn software as root to burn data ?
no, its not success burn, I can read the CD but some data are currepted

---

### Post by taygan on 2005-04-07
Hmm.. I've had problems when there are command characters in filenames.  Make sure you don't have any " or & or extra spaces, etc, that might be confusing cdrecord.

---

### Post by tofudrifter on 2005-08-31
i have this problem burning iso's
i have tried k3b, nautilus, gnomebaker

-k3b spits out 'unknown error 254'
-nautilus spits out 'burn completed' but when you try the cd it will appear to be a blank, and k3b will se said cd as appendable.
-gnomebaker burns a corrupt cd (edit: i get roughly the same error as jad)

---

