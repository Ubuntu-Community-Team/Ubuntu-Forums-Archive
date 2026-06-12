---
title: "Unable to burn CDs with Ubuntu"
date: 2005-02-03
forum: Desktop Environments
---

### Post by timelord726 on 2005-02-03
Hello everyone.  I'm a new Ubuntu user -- just moved over from Fedora Core 3 and loving every minute of it.  :)

Anyway, I am unable to burn CDs of any kind with any software program.  I have tried K3b and Graveman, and I'm stuck.  I'd like to be able to burn a CD with Ubuntu -- otherwise I am limited on what I can do.  There's already been two separate occasions where I myself or a friend of mine have needed a burned CD, and I have been unable to do it either time.

The most recent time has been an audio CD.  K3b seems to work for a while, until it says "Unlocking drive..." at which point it fails with "Error!"

Here's the debugging output:

```
System
-----------------------
K3b Version:0.11.18 
KDE Version: 3.2.3
QT Version: 3.2.3

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.8.1-4-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Warning: Linux-2.6.8 introduced incompatible interface changes.
/usr/bin/cdrecord: Warning: SCSI transport does no longer work for suid root programs.
/usr/bin/cdrecord: Warning: if cdrecord fails, try to run it from a root account.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-RW 48X16     '
Revision       : 'A.NZ'
Device seems to be: Generic CD-ROM.
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   : 
Supported modes: 
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
/usr/bin/cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
/usr/bin/cdrecord: Warning: controller returns wrong size for CD capabilities page.
pregap1: -1
/usr/bin/cdrecord: Drive does not support SAO recording.
/usr/bin/cdrecord: Illegal write mode for this drive.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=16 -dao driveropts=burnfree -eject -useinfo -pad -shorttrack -audio /tmp/kde-root/k3b_audio_Trudy's Theme0_01.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_02.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_03.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_04.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_05.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_06.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_07.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_08.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_09.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_10.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_11.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_12.inf /tmp/kde-root/k3b_audio_Trudy's Theme0_13.inf 
``` 

K3b is running with the gksudo command, so root access should be granted.  Any idea what's wrong with my setup?

Thanks in advance, and thanks for a wonderful distro!

---

