---
title: "Burning on a combo drive + laptop"
date: 2006-07-13
forum: Desktop Environments
---

### Post by SYSDmg on 2006-07-13
So everything is working finally in my ubuntu install except for cd burning, dvd burning works fine. I have a toshiba satellite m100-jg2 (core duo gig of ram intel gma all that fun stuff) the burner is a "scsi" burner i suppose (sata) and I have not for the life of me been able to figure out how to get just plain old cd burning to work.... heres my k3b error log:




System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
HL-DT-ST DVDRAM GMA-4082N HV02 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 183380

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
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
Revision       : 'HV02'
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
Drive DMA Speed: 13696 kB/s 77x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data   358 MB        
Total size:      411 MB (40:45.09) = 183382 sectors
Lout start:      411 MB (40:47/07) = 183382 sectors
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
Blocks total: 359847 Blocks current: 359847 Blocks remaining: 176465
Starting to write CD/DVD at speed 16 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  358 MB written.
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
Writing  time:   16.930s
Average write speed 145.1x.
Fixating...
Fixating time:   27.727s
/usr/bin/X11/cdrecord: fifo had 70 puts and 7 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 2 times full, min fill was 93%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=16 -tao driveropts=burnfree -eject -multi -xa -tsize=183380s - 

mkisofs
-----------------------
183380
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Using WINDOWS_XP_TO_MEDIA_CENTER_000.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N18.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N17.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_001.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N17.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N16.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_002.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N16.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N15.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_003.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N15.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N14.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_004.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N14.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N13.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_005.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N13.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N12.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_006.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N12.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N11.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_007.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N11.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N10.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_008.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.N10.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE9.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_009.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE9.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE8.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00A.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE8.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE7.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00B.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE7.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE6.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00C.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE6.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE5.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00D.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE5.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE4.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00E.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE4.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE3.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00F.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE3.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE2.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00G.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE2.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE1.rar)
Using WINDOWS_XP_TO_MEDIA_CENTER_00H.;1 for  /Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NE1.rar (Windows.XP.to.Media.Center.Edition.2005.Converter-NEUTEK.NET.exe)
  0.28% done, estimate finish Wed Jul 12 23:18:50 2006
  0.55% done, estimate finish Wed Jul 12 23:18:50 2006
  0.82% done, estimate finish Wed Jul 12 23:18:50 2006
  1.09% done, estimate finish Wed Jul 12 23:18:50 2006

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid MCE Upgrade -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sysdmg/k3bULx6va.tmp -rational-rock -hide-list /tmp/kde-sysdmg/k3bkJZW7a.tmp -joliet -hide-joliet-list /tmp/kde-sysdmg/k3bqNZoGa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-sysdmg/k3boGA10a.tmp

---

### Post by puccaso on 2006-08-01
ok
this is my problem
any ideas?


```
 

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-23-386
Devices
-----------------------
UNKNOWN DVD+RW RW8160 1.03 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+RW] [DVD-ROM; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=8 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-23-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM


```

---

