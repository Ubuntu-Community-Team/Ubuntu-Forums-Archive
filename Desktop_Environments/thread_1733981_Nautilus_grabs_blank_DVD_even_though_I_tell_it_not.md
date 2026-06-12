---
title: "Nautilus grabs blank DVD even though I tell it not to."
date: 2011-04-19
forum: Desktop Environments
---

### Post by Nutria on 2011-04-19
Maverick Meerkat.

In Nautilus->Preferences->Media, I uncheck both "Never prompt or start programs on media insertion" and "Browse media when inserted".

Yet, when I insert a blank DVD, GNOME still pops an icon onto the desktop.

I think that's preventing wodim from working.  Anyone have thoughts about what's going on?

Thanks.

```
$ wodim dev=/dev/dvd driveropts=burnfree -v -data foo.iso
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/dvd'
devname: '/dev/dvd'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ASUS    '
Identification : 'DRW-1814BLT     '
Revision       : '1.13'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x002B (DVD+R/DL)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) (current)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1048576 = 1024 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  7985 MB        
Total size:     9170 MB (908:33.80) = 4088535 sectors
Lout start:     9171 MB (908:35/60) = 4088535 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 4173824 Blocks current: 4173824 Blocks remaining: 85289
Speed set to 2770 KB/s
Starting to write CD/DVD at speed   2.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 3E 62 D7 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 41.880s timeout 40s
wodim: Cannot open new session.
Writing  time:   41.915s
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
```

---

