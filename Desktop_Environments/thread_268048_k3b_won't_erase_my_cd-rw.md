---
title: "k3b won't erase my cd-rw"
date: 2006-09-29
forum: Desktop Environments
---

### Post by TheRingmaster on 2006-09-29
I am trying to erase my cd-rw and it won't do it. here is the debugging output.

```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.4
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
HL-DT-ST CD-ROM GCR-8480B 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-ROM] [CD-ROM] [None]

UNKNOWN CD-R/RW RW7120A 1.22 (/dev/hdd, ) at  [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R96R]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=10 -tao -eject blank=all -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
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
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : '        '
Identifikation : 'CD-R/RW RW7120A '
Revision       : '1.22'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 2752512 = 2688 KB
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 00 00 00
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Waiting for drive to calm down.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0C 00 00 00 00 09 02 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x02 (focus servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 553.287s timeout 9600s
Performing OPC...
/usr/bin/X11/cdrecord: OPC failed.
Blanking entire disk
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0C 00 00 00 00 09 02 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x02 (focus servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 533.660s timeout 9600s
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.

```

---

### Post by doobit on 2006-09-29
> **jpazindustries said:**
> I am trying to erase my cd-rw and it won't do it. here is the debugging output.

ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 00 00 00

Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.


status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0C 00 00 00 00 09 02 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x02 (focus servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 533.660s timeout 9600s
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
[/CODE]

Did you try it at the 4x speed? Looks like it's having hardware trouble at 10X.

---

### Post by TheRingmaster on 2006-09-29
I'll try it now

EDIT: That did the trick thanks

---

