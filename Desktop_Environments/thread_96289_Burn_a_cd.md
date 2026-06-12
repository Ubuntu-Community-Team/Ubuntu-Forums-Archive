---
title: "Burn a cd"
date: 2005-11-28
forum: Desktop Environments
---

### Post by lisbet on 2005-11-28
Hello.
I have tried in many hours now to figure out how to burn a cd.
I have tried Graveman, Nerolinux, Serpentine, Gnomebaker and K3b.
I have also read others problems here on ubuntuforums.
However, I am lost... 

 Gnomebaker fails and output:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
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
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'DVD SOHD-167T   '
Revision       : '9S14'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0000
Profile: 0x0010 
Profile: 0x0008 

Can anyone help? Or "translate" this for me, so I understand what I should do?
Thanx in advance

---

### Post by taurus on 2005-11-28
Just a quick question.  Are you trying to burn a CD as a regular user or as root???  What if you do 

sudo k3b

---

### Post by lisbet on 2005-11-28
I did it without the sudo.
If I try to run k3b, while I am superuser.
I still have a problem here, that when I press on make anAudioCD and then drag the mp3-files inside, it says : Unable to handle the following files due to an unsupported format

:confused:

---

### Post by lisbet on 2005-11-28
I wonder...
In Devices under Options:
it says that I have no writer - devices....
only reader devices...
I might be there, the problem is.

Thanx, I will return, when I have done some shopping.

---

### Post by annsachd on 2006-02-05
I love shopping. It fixes just about everything.

---

