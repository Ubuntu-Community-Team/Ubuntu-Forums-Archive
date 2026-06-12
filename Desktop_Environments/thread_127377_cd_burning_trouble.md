---
title: "cd burning trouble"
date: 2006-02-08
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-02-08
My cd Burner, which i am not sure if it even works, mounts as "CD-RW Drive" so i assume that it is the burner, right.  Whenever i try to burn anything i get this error. Any help woudl be appreciated!

```
System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.5.0
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
LITE-ON LTR-48247S PPB1 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

JLMS XJ-HD166S DPS7 (/dev/hdd, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
K3b
-----------------------
Size of filesystem calculated: 4041

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'LTR-48247S      '
Revision       : 'PPB1'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1895168 = 1850 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data     7 MB        
Total size:        9 MB (00:53.90) = 4043 sectors
Lout start:        9 MB (00:55/68) = 4043 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 355805
Forcespeed is OFF.
Starting to write CD/DVD at speed 16 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
/usr/bin/X11/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x4 (CONDITION MET/GOOD)
cmd finished after 64.525s timeout 60s
/usr/bin/X11/cdrecord: OPC failed.
Writing  time:   65.765s
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -tao driveropts=burnfree -eject -multi -xa -tsize=4041s - 

mkisofs
-----------------------
4041
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
 12.65% done, estimate finish Wed Feb  8 19:56:01 2006
 24.92% done, estimate finish Wed Feb  8 19:56:01 2006
 37.19% done, estimate finish Wed Feb  8 19:56:03 2006
 49.86% done, estimate finish Wed Feb  8 19:56:03 2006

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-crowell/k3b8KYL4b.tmp -rational-rock -hide-list /tmp/kde-crowell/k3bur0zKb.tmp -joliet -hide-joliet-list /tmp/kde-crowell/k3bWQejkc.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-crowell/k3b9XiLEb.tmp 


```

---

### Post by olafura on 2006-02-09
Are you shure you are in the cdrom group.
You can do sudo addgroup username cdrom
If that doesn't work have you tried running k3b in sudo

Olafur Arason

---

### Post by %hMa@?b&lt;C on 2006-02-09
already a member of cdrom
ran as root, still same error
System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.5.0
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
LITE-ON LTR-48247S PPB1 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

JLMS XJ-HD166S DPS7 (/dev/hdd, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
K3b
-----------------------
Size of filesystem calculated: 13414

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.12-9-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'LTR-48247S      '
Revision       : 'PPB1'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1895168 = 1850 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data    26 MB        
Total size:       30 MB (02:58.88) = 13416 sectors
Lout start:       30 MB (03:00/66) = 13416 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 346432
Forcespeed is OFF.
Starting to write CD/DVD at speed 48 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
/usr/bin/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x4 (CONDITION MET/GOOD)
cmd finished after 64.733s timeout 60s
/usr/bin/cdrecord: OPC failed.
Writing  time:   65.967s
/usr/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=48 -tao driveropts=burnfree -eject -multi -xa -tsize=13414s - 

mkisofs
-----------------------
13414
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  3.81% done, estimate finish Thu Feb  9 16:35:02 2006
  7.51% done, estimate finish Thu Feb  9 16:34:23 2006
 11.20% done, estimate finish Thu Feb  9 16:34:10 2006
 15.02% done, estimate finish Thu Feb  9 16:34:03 2006

mkisofs command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-crowell/k3bCQxFwb.tmp -rational-rock -hide-list /tmp/kde-crowell/k3b5gmPCa.tmp -joliet -hide-joliet-list /tmp/kde-crowell/k3bEECe2a.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-crowell/k3bJoqgzb.tmp

---

### Post by olafura on 2006-02-10
Try using burn:/// in nautilus

Olafur Arason

---

### Post by %hMa@?b&lt;C on 2006-02-13
still doesn't work.  What could be the problem?

---

### Post by 8bit on 2006-02-14
I'm having the same problem; OPC Failed when trying to write to a CD. I've got a feeling that it has something to do with the new kernel 2.6.12 in the repositories. 

I've had problems with CD/DVD burning in the past after updating the kernel.

Can anyone else confirm this?

---

### Post by ahlich on 2006-02-15
Same here.

I have some info that might help:  have Ubuntu running on  2 desktops. Both had previously burned discs without a single problem, eventually they both stopped.  Today i  happened to try Kubuntu on one of them cause my wife likes KDE better but later re-installed Ubuntu. o it happens that that machine now burns CD's normally again. Now the difference between my machines if we consider substantial age differences (and therefore hardware) is the fact that the one that does not burn CD's is up-to-date...

Anyone...?

---

### Post by ahlich on 2006-02-15
Wait a sec!
(It's me again)

I just got rido of K3B and now it works on the other machine too!!

---

### Post by souki on 2006-02-16
silly question but, do you have enough space on /tmp ?
if not, change the default temporary directory (misc settings)

---

### Post by %hMa@?b&lt;C on 2006-02-17
how wouldl i change that. I dont think that size is a problem, becuase it doesnt even work on tiny files, like 1 mb.

---

