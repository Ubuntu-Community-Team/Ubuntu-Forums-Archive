---
title: "Cdrecord problems!"
date: 2005-02-10
forum: Desktop Environments
---

### Post by Alessio on 2005-02-10
What's this problem?

alessio@Ubuntu:/media $ cdrecord -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-2-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
alessio@Ubuntu:/media $ sudo cdrecord -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-2-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by m4ng0 on 2005-02-10
Try:
sudo cdrecord dev=ATA -scanbus

---

### Post by kleeman on 2005-02-10
Hmmm this looks like a bug I reported a while bit to do with scsi cd drives. My problem was that hotplug did not automatically load the sg module when it saw a scsi drive. I got round it with

sudo modprobe sg

and for a permanent fix put sg in /etc/modules

Might work  \\:D/

---

### Post by Alessio on 2005-02-11
alessio@Ubuntu:~ $ sudo cdrecord dev=ATA -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-2-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.

-------------------

After the modprobe.. i have the same error. It isn't fix.

---

### Post by kleeman on 2005-02-11
What hardware do you have?
Did you try the "sudo modprobe sg"?
Here is the equivalent output on my box after this modprobe: (before it was similar to yours)

[richard@dual richard]$  sudo cdrecord dev=ATA -scanbus
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'LITE-ON ' 'DVD SOHD-167T   ' '9S13' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

---

### Post by cblack on 2005-02-11
Looks to be a problem with the version of cdrecord in Hoary. I'm having the same issues as well.

---

### Post by cblack on 2005-02-11
And there's already been a bug report. See:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2023](https://bugzilla.ubuntu.com/show_bug.cgi?id=2023)

---

