---
title: "Problem with cdrecord &amp; cdrdao"
date: 2006-04-22
forum: Desktop Environments
---

### Post by cflam69 on 2006-04-22
Hello,
First, I want to say that I'm not english, so ... :???: 
I have a problem with cdrecord and cdrdao because I can't erase my cdrw with Ubuntu 5.10. My Cd burner is a samsung SW-212B on a desktop.
I search a solution on google and on other Linux's forums but ](*,) 
Some information :
```
sudo cdrecord -v -force -speed=8 -dev=/dev/hdd -blank=all
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SAMSUNG '
Identifikation : 'CD-R/RW SW-212B '
Revision       : 'P000'
Device seems to be: Generic mmc CD-RW.
Current: 0x0000
Profile: 0x0008
Profile: 0x0009
Profile: 0x000A
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96R
Current Secsize: 0
cdrecord: Success. read disk info: scsi sendcmd: no error
CDB:  51 00 00 00 00 00 00 00 04 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 4
cmd finished after 0.000s timeout 240s
cdrecord: Cannot get disk type.
Waiting for drive to calm down.
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 40s
Starting to write CD/DVD at speed 8 in real force BLANK mode for single session.Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 9600s
Starting to write CD/DVD at speed 8 in real force BLANK mode for single session.No chance to quit anymore. Operation starts.
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 40s
Performing OPC...
cdrecord: OPC failed.
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 40s
Blanking entire disk
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 9600s
cdrecord: Cannot blank disk, aborting.
```

And scanbus :
```
cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
```

And lshw 
```
-cdrom:1
                   product: SAMSUNG CD-R/RW DRIVE SW-212B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet 
```

I hope someone can help me because I hate erase my cdrw on my Wife's iMac ! :p 

Thanks !

---

### Post by cflam69 on 2006-04-24
A little up because I'm totally lost ...

---

