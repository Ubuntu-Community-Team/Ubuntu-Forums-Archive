---
title: "Can not burn cds"
date: 2009-02-22
forum: General Help
---

### Post by rhaynal on 2009-02-22
Hi,

I am using Ubuntu 8.10. I have been having all kinds of problems reading and writing audio cds. I believe I have solved the reading part, that is I can rip cds now that play but I cannot burn cds that work.

I have searched the Internet and have tried numerous fixes and additional software but nothing seems to help. I have added the repositories from mediabuntu and have installed all the codecs. I have tried Brasero, K3B, Gnomebaker but none of will work.

I use to have Ubuntu 8.04 on this computer until my hard disk crashed. After the crash I decided to go with 8.10. The reason I bring this up is that 8.04 was able to read and wriet to the cd fairly easy and I don't remember putting this much time trying to figure it out.

Can someone point me in the right direction? Here is the output of GnomeBaker:

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DW-D22A  '
Revision       : 'BYS2'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1895168 = 1850 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1411 KB/s
:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 130565
Forcespeed is OFF.
Starting to write CD/DVD at speed   8.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds. 4 seconds. 3 seconds. 2 seconds. 1 seconds. 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 00 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 61.188s timeout 60s
wodim: OPC failed.
Writing  time:   64.339s
BURN-Free was never needed.
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

---

