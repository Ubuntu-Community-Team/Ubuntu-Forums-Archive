---
title: "Problem with writing cd"
date: 2006-01-02
forum: Desktop Environments
---

### Post by LordMelkor on 2006-01-02
When I used k3b to burn a Data CD I got the error that k3b was unable to 'fixate the disc'... and then ejected the CD after about 1 second. The debugging output is as follows:

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LG CD-RW CED-8080B 1.04 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 269162

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-386
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
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'LG      '
Identifikation : 'CD-RW CED-8080B '
Revision       : '1.04'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1024000 = 1000 KB
Drive DMA Speed: 99249 kB/s 563x CD 71x DVD
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   525 MB        
Total size:      603 MB (59:48.85) = 269164 sectors
Lout start:      604 MB (59:50/64) = 269164 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11849 (97:24/01)
  ATIP start of lead out: 359847 (79:59/72)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 25
Manufacturer: Taiyo Yuden Company Limited
Blocks total: 359847 Blocks current: 359847 Blocks remaining: 90683
Starting to write CD/DVD at speed 2 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  525 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 20.778s timeout 40s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   25.825s
Average write speed 139.1x.
Fixating...
/usr/bin/X11/cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 2C 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x04 (current program area is empty) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 480s
cmd finished after 0.001s timeout 480s
/usr/bin/X11/cdrecord: Cannot fixate disk.
Fixating time:    0.019s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=2 -tao -eject -multi -xa -tsize=269162s - 

mkisofs
-----------------------
269162
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.19% done, estimate finish Sun Jan  1 22:57:29 2006
  0.37% done, estimate finish Sun Jan  1 22:53:00 2006
  0.56% done, estimate finish Sun Jan  1 22:51:32 2006
  0.74% done, estimate finish Sun Jan  1 22:50:48 2006
/usr/bin/X11/mkisofs: Connection reset by peer. cannot fwrite 32768*1

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid Anime_Music -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher Krishanu Ray -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-krishanu/k3b3ZsYFa.tmp -rational-rock -hide-list /tmp/kde-krishanu/k3bBCNSfa.tmp -joliet -hide-joliet-list /tmp/kde-krishanu/k3brKxkTb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-krishanu/k3bMVUXfc.tmp 


I am very new to linux and any assistance would be greatly appreciated. Thanks!

---

### Post by LordMelkor on 2006-01-02
per the suggestions of some on IRC I logged in as the root user, but got the same error:

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LG CD-RW CED-8080B 1.04 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 269162

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'LG      '
Identifikation : 'CD-RW CED-8080B '
Revision       : '1.04'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1024000 = 1000 KB
Drive DMA Speed: 115200 kB/s 654x CD 83x DVD
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Track 01: data   525 MB        
Total size:      603 MB (59:48.85) = 269164 sectors
Lout start:      604 MB (59:50/64) = 269164 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11849 (97:24/01)
  ATIP start of lead out: 359847 (79:59/72)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 25
Manufacturer: Taiyo Yuden Company Limited
Blocks total: 359847 Blocks current: 359847 Blocks remaining: 90683
Starting to write CD/DVD at speed 2 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  525 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 20.999s timeout 40s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   26.019s
Average write speed 138.0x.
Fixating...
/usr/bin/X11/cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 2C 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x04 (current program area is empty) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 480s
cmd finished after 0.000s timeout 480s
/usr/bin/X11/cdrecord: Cannot fixate disk.
Fixating time:    0.002s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=2 -tao -eject -multi -xa -tsize=269162s - 

mkisofs
-----------------------
269162
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.19% done, estimate finish Sun Jan  1 23:24:00 2006
  0.37% done, estimate finish Sun Jan  1 23:19:31 2006
  0.56% done, estimate finish Sun Jan  1 23:18:03 2006
  0.74% done, estimate finish Sun Jan  1 23:17:19 2006
/usr/bin/X11/mkisofs: Connection reset by peer. cannot fwrite 32768*1

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid Anime_Music -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher Krishanu Ray -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3bEE7uhb.tmp -rational-rock -hide-list /tmp/kde-root/k3b1P0adb.tmp -joliet -hide-joliet-list /tmp/kde-root/k3bgWPC8b.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-root/k3brvkxKa.tmp 

:sad: :-s

---

### Post by meborc on 2006-01-02
since it is a KDE related problem, maybe you are in the wrong place... try under the **kubuntu desktop support **forum, but have you tried any other programs for cd writing? gnomebaker for example?

---

### Post by LordMelkor on 2006-01-02
why is it a KDE problem.. I use gnome on Ubuntu Breezy....

---

### Post by ShirishAg75 on 2006-01-02
K3b is a KDE project. There is a possibiity that it might not have installed all the dependencies or such. Haven't tried K3b on Ubuntu also hence just guessing. What is better perhaps is gnomebaker or cdrecord on the  CLI.

---

