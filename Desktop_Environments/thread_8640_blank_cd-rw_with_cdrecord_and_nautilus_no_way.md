---
title: "blank cd-rw with cdrecord and nautilus: no way?"
date: 2004-12-19
forum: Desktop Environments
---

### Post by burlap on 2004-12-19
I have this TDK CD-RW700 cd I used to blank and record in my Aurox (2.4.22, with cdrdao, I do not remember version of the latter anymore). However, one of the reasons I switched to Ubuntu is that I did not want to have extra CLI tools for everything. But I had to install cdrdao (1:1.1.9-3 via synaptic) in my Ubuntu - it works fine (blanks this cd, "minimal" mode). Here is, what I get with cdrecord (blank=minimal does not work, of course, it suggests to run blank=all):
```
sudo cdrecord -force blank=all dev=/dev/hdd
Password:
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'QSI     '
Identifikation : 'CDRW/DVD SBW-241'
Revision       : 'VX09'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Waiting for drive to calm down.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 9600s
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 9600s
cdrecord: Cannot blank disk, aborting.
```
Nautilus-cd-burner ("erase cd" option is missing?) does not blank the cd either - when I try to record data on this cd-rw it aborts instead of blanking. Xcdroast does not work (as it is cdrecord). I do not want to use k3b (I prefer to blank cds from CLI with cdrdao). 

Why cdrecord does not work?

---

### Post by burlap on 2004-12-22
Doesn't really anyone have problems with cd blanking? Or all of you use cdrdao and k3b?

---

### Post by nocturn on 2004-12-22
I will try to test this tonight with my burner, I only installed Ubuntu yesterday.

I know there are 'issues' with SCSI (real and emulated) burning on 2.6 kernels (specially 2.6.8 is affected badly)

My Gentoo box is also hit by this.

---

