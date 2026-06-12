---
title: "Can't Format a CD using Edgy"
date: 2006-10-29
forum: Desktop Environments
---

### Post by bennyj on 2006-10-29
Could some one tell me how to fix this.Im running ubuntu edgy and I cant seem to erase or format a cd-r anymore.I have tried both gnome baker and kb3.If i put a cd in the drive and try to erase I get this


System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
Memorex 52MAX 325216AJ NWK2 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Memorex 52X CD-ROM AJiA YWS2 (/dev/hdd, ) at  [CD-ROM] [CD-ROM] [None]
Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-386

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
/usr/bin/X11/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/X11/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/X11/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
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
Response Format: 2
Capabilities   : 
Vendor_info    : 'Memorex '
Identifikation : '52MAX 325216AJ  '
Revision       : 'NWK2'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1422080 = 1388 KB
/usr/bin/X11/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/X11/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12510 (97:15/15)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Forcespeed is OFF.
Waiting for drive to calm down.
Starting to write CD/DVD at speed 16 in real force BLANK mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Starting to write CD/DVD at speed 16 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 9600s
Performing OPC...
/usr/bin/X11/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Blanking PMA, TOC, pregap
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 9600s
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.

Thanks

---

### Post by clubsoda on 2006-12-19
> Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root? : Operation not permittedThat could be part of the problem.  I think you need to reconfigure cdrecord or start the burning application from the command line via sudo.  But I guess you've already sorted this out by now.

The reason I'm reviving this thread is that I'm getting a similar error that bennyj got:-```
cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
[COLOR="Red"]cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD write parameter page.[/COLOR]
cdrecord: Warning: controller returns wrong size for CD write parameter page.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
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
Vendor_info    : 'LG      '
Identifikation : 'CD-RW CED-8042B '
Revision       : '1.05'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1024000 = 1000 KB
cdrecord: Warning: controller returns wrong size for CD write parameter page.
cdrecord: Warning: controller returns wrong size for CD write parameter page.
cdrecord: Warning: controller returns wrong size for CD write parameter page.
cdrecord: Warning: controller returns wrong size for CD write parameter page.
cdrecord: Warning: controller returns wrong size for CD write parameter page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Trying to use high speed medium on low speed writer.
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11635 (97:26/65)
  ATIP start of lead out: 337350 (75:00/00)
  1T speed low:  4 1T speed high: 10
  power mult factor: 1 5
  recommended erase/write power: 3
  A1 values: 24 1A BC
  A2 values: 00 00 00
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation

```The above is the output from XfBurn when trying to blank a CD-RW without force.  No error messages but no action from the drive either.  Using the "force" option the drive appears to blank a CD-RW but there's nothing I can do to make it write data to a disc.

With Xubuntu I can't even play an audio CD in this drive.  The drive is old but has the latest firmware upgrade.  Worked flawlessly in Slackware 10.1 (2.4 series kernel) and of course works perfectly in Windows.

I've read probably 20 different threads with conflicting advice about this but still no solution.  Any suggestions?

---

