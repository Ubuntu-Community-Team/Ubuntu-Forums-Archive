---
title: "k3b update"
date: 2006-09-22
forum: Desktop Environments
---

### Post by missmoondog on 2006-09-22
had an update to k3b this morning. now i get errors ersing cd-rw and burning cd-r. here's what the debugging log show after trying to burn a cd-r. made it through 2 songs then closed session and errored out. anybody else having problems? anybody have a clue as to what to do? have never had issues with this before. 

thanks

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.4
QT Version:  3.3.6
Kernel:      2.6.15-27-686
Devices
-----------------------
ATAPI CD-R/RW 16X10 G.DF (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; RAW/R16; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
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
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-R/RW 16X10   '
Revision       : 'G.DF'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R16 RAW/R96R
Drive buf size : 1630208 = 1592 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   71 MB (07:05.36) no preemp swab copy
Track 02: audio   58 MB (05:45.73) no preemp swab copy
Track 03: audio   60 MB (06:01.82) no preemp swab copy
Track 04: audio   75 MB (07:29.78) no preemp swab copy
Track 05: audio   46 MB (04:34.78) no preemp swab copy
Track 06: audio   55 MB (05:28.29) no preemp swab copy
Track 07: audio   43 MB (04:19.80) no preemp swab copy
Track 08: audio   37 MB (03:41.78) no preemp swab copy
Track 09: audio   47 MB (04:43.85) no preemp swab copy
Track 10: audio   60 MB (06:00.52) no preemp swab copy
Track 11: audio   98 MB (09:42.58) no preemp swab copy
Track 12: audio   79 MB (07:51.57) no preemp swab copy
Track 13: audio   50 MB (04:59.86) no preemp swab copy
Total size:      788 MB (78:09.77) = 351733 sectors
Lout start:      789 MB (78:11/58) = 351733 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 7
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11646 (97:26/54)
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 10
Manufacturer: Lead Data Inc.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 8116
Starting to write CD/DVD at speed 12 in real TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   71 MB written.
Track 01:    1 of   71 MB written (fifo  78%) [buf  57%]   0.2x.
Track 01:    2 of   71 MB written (fifo 100%) [buf  99%]   4.6x.
Track 01:    3 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    4 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    5 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    6 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    7 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    8 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    9 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   10 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   11 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   12 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   13 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   14 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   15 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   16 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   17 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   18 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   19 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   20 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   21 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   22 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   23 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   24 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   25 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   26 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   27 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   28 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   29 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   30 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   31 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   32 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   33 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   34 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   35 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   36 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   37 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   38 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   39 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   40 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   41 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   42 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   43 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   44 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   45 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   46 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   47 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   48 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   49 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   50 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   51 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   52 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   53 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   54 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   55 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   56 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   57 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   58 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   59 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   60 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   61 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   62 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   63 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   64 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   65 of   71 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   66 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   67 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   68 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   69 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01:   70 of   71 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   71 of   71 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01: Total bytes read/written: 75033504/75033504 (31902 sectors).
Starting new track at sector: 32054
Track 02:    0 of   58 MB written.
Track 02:    1 of   58 MB written (fifo  78%) [buf  57%]  66.2x.
Track 02:    2 of   58 MB written (fifo 100%) [buf  99%]   3.7x.
Track 02:    3 of   58 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:    4 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:    5 of   58 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:    6 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:    7 of   58 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:    8 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:    9 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   10 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   11 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   12 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   13 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   14 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   15 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   16 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   17 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   18 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   19 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   20 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   21 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   22 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   23 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   24 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   25 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   26 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   27 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   28 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   29 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   30 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   31 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   32 of   58 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   33 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   34 of   58 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   35 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   36 of   58 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   37 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   38 of   58 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   39 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   40 of   58 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   41 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   42 of   58 MB written (fifo 100%) [buf  99%]   4.0x.
Track 02:   43 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   44 of   58 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:   45 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   46 of   58 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:   47 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   48 of   58 MB written (fifo 100%) [buf  99%]   4.3x.
Track 02:   49 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   50 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   51 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   52 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   53 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   54 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   55 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   56 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02:   57 of   58 MB written (fifo 100%) [buf  99%]   4.1x.
Track 02:   58 of   58 MB written (fifo 100%) [buf  99%]   4.2x.
Track 02: Total bytes read/written: 60987360/60987360 (25930 sectors).
Trouble flushing the cache
Writing  time:  234.431s
Average write speed  20.0x.
Min drive buffer fill was 57%
Fixating...
/usr/bin/X11/cdrecord: Success. flush cache: scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 02 FF 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x02 Qual 0xFF (no seek complete) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 13.257s timeout 120s
/usr/bin/X11/cdrecord: Cannot close track.
Fixating time:   74.595s
/usr/bin/X11/cdrecord: fifo had 2206 puts and 2143 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 2079 times full, min fill was 57%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=12 -tao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-cork/k3b_audio_0_01.inf /tmp/kde-cork/k3b_audio_0_02.inf /tmp/kde-cork/k3b_audio_0_03.inf /tmp/kde-cork/k3b_audio_0_04.inf /tmp/kde-cork/k3b_audio_0_05.inf /tmp/kde-cork/k3b_audio_0_06.inf /tmp/kde-cork/k3b_audio_0_07.inf /tmp/kde-cork/k3b_audio_0_08.inf /tmp/kde-cork/k3b_audio_0_09.inf /tmp/kde-cork/k3b_audio_0_10.inf /tmp/kde-cork/k3b_audio_0_11.inf /tmp/kde-cork/k3b_audio_0_12.inf /tmp/kde-cork/k3b_audio_0_13.inf

---

### Post by RevJack on 2006-09-22
After the k3b update, k3b now freezes when trying to burn a CD. This is NOT good!

---

