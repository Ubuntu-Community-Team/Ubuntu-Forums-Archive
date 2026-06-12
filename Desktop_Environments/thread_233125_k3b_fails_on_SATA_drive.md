---
title: "k3b fails on SATA drive"
date: 2006-08-09
forum: Desktop Environments
---

### Post by sfabel on 2006-08-09
Hi everybody,

I've recently purchased a Lenovo 3000 N100 Laptop which is quite cool, but there are several issues, the most pressing one being that I am not able to burn a CD-ROM, a DVD or a double-layer DVD.

This is the error k3b gives me:

```
System
-----------------------
K3b Version: 0.12.16

KDE Version: 3.5.4
QT Version:  3.3.6
Kernel:      2.6.15-26-686
Devices
-----------------------
HL-DT-ST DVDRAM GMA-4082N HA01 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-Rom; DVD-Rom; DVD-Ram; DVD-R; DVD-RW; and so on (double layer, etc.) - I've shortened this for space issues]

K3b
-----------------------
Size of filesystem calculated: 3802873

Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: splitting layers at 1901440 blocks
**:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=7h/ASC=00h/ACQ=D0h]: Input/output error**

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:3802873 -dvd-compat -speed=2.4 

mkisofs
-----------------------
Warning: creating filesystem that does not conform to ISO-9660.
Warning: ISO-9660 filenames longer than 31 may cause buffer overflows in the OS.

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid Backup 09-08-2006 -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher 
```

I've highlighted the error message. If you guys have *any* idea what I could do to fix the problem, please let me know.

This page was one of the primary reasons to buy the thing, as the auther recommended it as a "top notch" linux laptop. It is, but without a burner, it's pretty useless.
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100")

I also have no idea why my Kubuntu sees two devices for one physical drive, i.e. /dev/scd0 and /dev/sg1.

On a side note, neither the included fingerprint reader, nor the embedded web cam works as there are no drivers out there for Linux (or they don't compile).

Thanks for any information.

Stephan

---

### Post by sfabel on 2006-08-09
While the above was for DVD burning, here is another debug output for CD-ROM burning:

```
System
-----------------------
K3b Version: 0.12.16

KDE Version: 3.5.4
QT Version:  3.3.6
Kernel:      2.6.15-26-686
Devices
-----------------------
HL-DT-ST DVDRAM GMA-4082N HA01 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-Rom; DVD-Rom; DVD-Ram; DVD-R; DVD-RW; ...]

K3b
-----------------------
Size of filesystem calculated: 117747

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?   **(YES)**
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
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GMA-4082N'
Revision       : 'HA01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13638 kB/s 77x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   229 MB        
Total size:      264 MB (26:09.98) = 117749 sectors
Lout start:      264 MB (26:11/74) = 117749 sectors
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
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 242096
Starting to write CD/DVD at speed 24 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  229 MB written.
/usr/bin/X11/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 BA 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.016s timeout 40s
/usr/bin/X11/cdrecord: The current problem looks like a buffer underrun.
/usr/bin/X11/cdrecord: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/X11/cdrecord: Please report.
/usr/bin/X11/cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 380928 bytes
Writing  time:   15.551s
Average write speed 101.5x.
Fixating...
Fixating time:   28.628s
/usr/bin/X11/cdrecord: fifo had 70 puts and 7 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 2 times full, min fill was 92%.
...

```

Stephan

---

### Post by mzilhao on 2006-08-10
well, i too have a SATA drive (and an LG burner) and i'm having the same issue. here's the error:
```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4160B A301 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
/usr/bin/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
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
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A301'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 
Profile: 0x000A (current)
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13755 kB/s 78x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data    49 MB        
Total size:       56 MB (05:36.21) = 25216 sectors
Lout start:       56 MB (05:38/16) = 25216 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11615 (97:27/10)
  ATIP start of lead out: 96600 (21:30/00)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 4 5
  recommended erase/write power: 3
  A1 values: 02 4A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 96600 Blocks current: 96600 Blocks remaining: 71384
Starting to write CD/DVD at speed 4 in dummy SAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Sending CUE sheet...
/usr/bin/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.016s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of   49 MB written.
/usr/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.020s timeout 200s
/usr/bin/cdrecord: A write error occured.
/usr/bin/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   66.992s
Average write speed   5.0x.
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.004s
/usr/bin/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=4 -dao -dummy driveropts=burnfree -eject -data /home/shared/Downloads/distros/DamnSmallLinux.iso 


```

i've googled around and eventually given up. i'll burn cds with nautilus...
there's a similar thread [here]("http://www.ubuntuforums.org/showthread.php?t=217472").
anyway, i'd love to know the answer to this as well.

---

### Post by mzilhao on 2006-08-27
sfabel, did you manage to solve this problem? 
i kind of gave up, but i'd be very interested if someone has a solution...

---

### Post by sfabel on 2006-08-30
No solution yet.

Here's additional output from my syslog, although not while burning, but while ripping a CD. I'm also experiencing problems mounting an external USB drive with FAT file system on it (the file system gets mounted read-only and a fsck.vfat gives an error).

Here's my /var/log/syslog:
```

30.08.2006 10:51:30	localhost	kernel	[17246564.508000] printk: 275 messages suppressed.
30.08.2006 10:51:30	localhost	kernel	[17246564.508000]    program kio_audiocd not setting count and/or reply_len properly
30.08.2006 10:51:30	localhost	kernel	[17246564.508000] sg_write: data in/out 30576/30576 bytes for SCSI command 0xbe--guessing data in;

```

It also takes **forever** when I enter a CD, to make the dialogue appear as to what I want to do with this disc (I'm on Kubuntu).

This is REALLY annoying.

Stephan

---

### Post by mzilhao on 2006-09-08
this may be the solution we were hoping for:
[http://ubuntuforums.org/showthread.php?t=252719](http://ubuntuforums.org/showthread.php?t=252719)

i've just made a quick test and it worked!

---

