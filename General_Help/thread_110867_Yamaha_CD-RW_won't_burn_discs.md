---
title: "Yamaha CD-RW won't burn discs"
date: 2005-12-31
forum: General Help
---

### Post by Sherwood Shark on 2005-12-31
Hi,
New to Linux and loving Ubuntu except i cannot get my cd-rw drive to burn anything (data ormusic). Yamaha CRW-F1E in a P3 800MHz machine running Breezy. I can read from the drive, just not write with Gnome-baker or Sepentine. 
Error message I get from Gnome-baker is:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent
defaults. cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-686 cdrecord: There are
unsettled issues with Linux-2.5 and newer. cdrecord: If you have
unexpected problems, please try Linux-2.4 or Solaris. cdrecord: Operation
not permitted. WARNING: Cannot set RR-scheduler cdrecord: Permission
denied. WARNING: Cannot set priority using setpriority(). cdrecord:
WARNING: This causes a high risk for buffer underruns. scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported. Linux sg
driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root? :
Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1
'@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J.
Schilling'). SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004
Joerg Schilling NOTE: this version of cdrecord is an inofficial (modified)
release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to
      <cdrtools@packages.debian.org>. The original author should not be
      bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'. atapi: 1
Device type    : Removable CD-ROM
Version        : 2
Response Format: 2
Capabilities   : SYNC
Vendor_info    : 'YAMAHA  '
Identifikation : 'CRW-F1E         '
Revision       : '1.0d'
Device seems to be: Generic mmc CD-RW. Current: 0x0009
Profile: 0x0008
Profile: 0x0009 (current)
Profile: 0x000A
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr). Driver flags   :
MMC-3 SWABAUDIO BURNFREE AUDIOMASTER FORCESPEED DISKTATTOO Supported
modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R Drive buf size : 7469952
= 7294 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using
setpriority(). cdrecord: WARNING: This causes a high risk for buffer
underruns. Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed
SUID root? : Operation not permitted
Track 01: data   656 MB         padsize:   30 KB Total size:      753 MB
(74:39.14) = 335936 sectors Lout start:      753 MB (74:41/11) = 335936
sectors Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3) ATIP start of
  lead in:  -11634 (97:26/66) ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar) Manuf.
index: 3
Manufacturer: CMC Magnetics Corporation Blocks total: 359846 Blocks
current: 359846 Blocks remaining: 23910 Forcespeed is OFF.
Starting to write CD/DVD at speed 8 in real TAO mode for multi session.
Last chance to quit, starting real write in 5 seconds.   4
seconds.   3 seconds.   2 seconds.  1 seconds.   0 seconds. Operation starts. Waiting for reader
process to fill input buffer ... input buffer ready. BURN-Free is OFF.
Performing OPC...
cdrecord: Success. send opc: scsi sendcmd: no error CDB:  54 01 00 00 00
00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00 Sense Key:
0x3 Medium Error, Segment 0 Sense Code: 0x73 Qual 0x03 (power calibration
area error) Fru 0x0 Sense flags: Blk 0 (not valid)
cmd finished after 10.694s timeout 60s cdrecord: OPC failed.
Writing  time:   13.661s
cdrecord: fifo had 64 puts and 0 gets. cdrecord: fifo was 0 times empty
and 0 times full, min fill was 100%.

Any ideas what I should do to fix this?  Get a new optical drive?
TIA!
Sherwood

---

### Post by steve.horsley on 2006-01-01
I know thsi sounds like cop-out, but try k3b instead. It's the only one that seems to work for me. Gnome-baker always burns coasters.


Another thing that might make a difference - see if DMA is enabled on your CD drive with the command **hdparm /dev/hdc**. If not, try enabling it with **sudo hdparm -d 1 /dev/hdc**. If DMA fixes it you can make this change permanent by adding the following to /etc/hdparm.conf:
```
/dev/hdc {
        dma = on
}
```

---

### Post by Sherwood Shark on 2006-01-01
I tried K3B and still no-go with the Yamaha.  I went and got a new Lite-on 1693S DVD-RW and it worked right out of the box for music and data cd, data dvd - whatever.  Jeez!  Just got tired of ](*,) - if you know what I mean!

I do **really** like K3B, so thanks for the tip! :p

SShark

---

