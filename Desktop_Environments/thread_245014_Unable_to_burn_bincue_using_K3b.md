---
title: "Unable to burn bin/cue using K3b"
date: 2006-08-27
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-27
K3b fails when it tries to send cue sheet. I'm not sure what the meaning is. Here is the debugging output.

```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
PIONEER DVD-RW  DVR-105 1.30 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
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
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-105 '
Revision       : '1.30'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data     1 MB        
Track 02: data   802 MB        
Total size:      803 MB (79:35.25) = 358144 sectors
Lout start:      803 MB (79:37/19) = 358144 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 1701
Starting to write CD/DVD at speed 16 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
/usr/bin/X11/cdrecord: Success. send_cue_sheet: scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 30 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 26 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x26 Qual 0x00 (invalid field in parameter list) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 48
cmd finished after 0.014s timeout 200s
/usr/bin/X11/cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/X11/cdrecord: Cannot send CUE sheet.
/usr/bin/X11/cdrecord: Could not write Lead-in.
Writing  time:    7.487s
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=16 -dao driveropts=burnfree cuefile=/home/veronica/Movie.cue -eject 


```

---

### Post by coolmdsguy on 2006-11-09
Hi, Were you able to find the cause of this bug and fix that?

I'm also getting a similar error

```

-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
PIONEER DVD-RW  DVR-105 1.10 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

MATSHITA DVD-ROM SR-8588 7E26 (/dev/hdd, ) at  [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
K3bVcdXml:
-----------------------
<?xml version="1.0"?>
<!DOCTYPE videocd PUBLIC "-//GNU//DTD VideoCD//EN" "http://www.gnu.org/software/vcdimager/videocd.dtd">
<videocd class="vcd" xmlns="http://www.gnu.org/software/vcdimager/1.0/" version="2.0" >
 <info>
  <album-id></album-id>
  <volume-count>1</volume-count>
  <volume-number>1</volume-number>
  <restriction>0</restriction>
 </info>
 <pvd>
  <volume-id>VIDEOCD</volume-id>
  <system-id>CD-RTOS CD-BRIDGE</system-id>
  <application-id>CDI/CDI_VCD.APP;1</application-id>
  <preparer-id>K3B - VERSION 0.12.17</preparer-id>
  <publisher-id>K3B - VERSION 0.12.17</publisher-id>
 </pvd>
 <filesystem>
  <folder>
   <name>SEGMENT</name>
  </folder>
 </filesystem>
 <sequence-items>
  <sequence-item id="sequence-000" src="/home/nsnarayanan/tovid/encoding/EM1.mpg" >
   <default-entry id="entry-000" />
  </sequence-item>
 </sequence-items>
 <pbc>
  <selection id="select-sequence-000" >
   <prev ref="end" />
   <next ref="end" />
   <return ref="end" />
   <timeout ref="end" />
   <wait>2</wait>
   <loop jump-timing="immediate" >1</loop>
   <play-item ref="sequence-000" />
  </selection>
  <endlist rejected="true" id="end" />
 </pbc>
</videocd>

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/X11R6/bin/cdrecord: Warning: Running on Linux-2.6.17-10-386
/usr/X11R6/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/X11R6/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/X11R6/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/X11R6/bin/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/X11R6/bin/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
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
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-105 '
Revision       : '1.10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data     1 MB        
Track 02: data   738 MB        
Total size:      739 MB (73:17.45) = 329809 sectors
Lout start:      740 MB (73:19/34) = 329809 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 30037
Starting to write CD/DVD at speed 16 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
/usr/X11R6/bin/cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
/usr/X11R6/bin/cdrecord: Success. send_cue_sheet: scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 30 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 26 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x26 Qual 0x00 (invalid field in parameter list) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 48
cmd finished after 0.014s timeout 200s
/usr/X11R6/bin/cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/X11R6/bin/cdrecord: Cannot send CUE sheet.
/usr/X11R6/bin/cdrecord: Could not write Lead-in.
/usr/X11R6/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/X11R6/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
Writing  time:    6.170s

cdrecord command:
-----------------------
/usr/X11R6/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -dao cuefile=/tmp/kde-root/VIDEOCD.cue -eject 

vcdxbuild command:
-----------------------
/usr/X11R6/bin/vcdxbuild --progress --gui --cue-file=/tmp/kde-root/VIDEOCD.cue --bin-file=/tmp/kde-root/VIDEOCD.bin /tmp/kde-root/k3bn5Wmna.tmp 

```

Any help to resolve this will be much appreciated. I am not able to burn any media because of this error :(

---

### Post by fakie_flip on 2006-11-09
I can't remember if this was for the same problem or a different one, but it fixed the problem I had a while back with k3b. My name on the forum there is the same here, fakie_flip.

[http://www.linuxquestions.org/questions/showthread.php?t=482680&highlight=k3bsetup](http://www.linuxquestions.org/questions/showthread.php?t=482680&highlight=k3bsetup)

---

### Post by fakie_flip on 2006-11-09
I had to change the permissions of a few binaries such as cdrecord and cdrdao, so that they would run as root and not the normal user. I think I used sticky bit.

---

### Post by tbooher on 2006-11-19
I did something like:

  112  sudo chmod 4755 /usr/bin/cdrecord
  113  sudo chmod 4755 /usr/bin/cdrecord.mmap
  114  sudo chmod 4755 /usr/bin/X11/cdrecord.mmap
  115  sudo chmod 4755 /usr/bin/cdrdao
  116  sudo chmod 4755 /usr/bin/X11/cdrdao

which cleared things up slightly, but i am still having problems.

---

### Post by ]Nbx*cmD[ on 2006-12-07
I usually convert them to iso, you can use plenty of programs for that. Particularly, I use bchunk (apt-get install bchunk).

```
 bchunk mybin.bin mycue.cue myiso 
```

the output will be a myiso.iso file ready to be burned.

---

### Post by xjgnsdof on 2007-08-20
Assuming that you have permission to modify the .bin and .cue files, all you have to do is change the filename and extension for each .bin and .cue file to upper case. Then, k3b will read the cue and burn the .bin just fine.

For example, I had three .cue and .bin pairs called "MAFIA1," "MAFIA2" and "MAFIA3" that all had lower case extensions. Once I changed the extension to upper case, the project completed successfully. I'm not sure if the entire filename also has to be upper case, but definitely the extensions should be.

---

