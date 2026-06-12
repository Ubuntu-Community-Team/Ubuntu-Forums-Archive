---
title: "Fail to write iso file from gnome"
date: 2008-01-28
forum: Desktop Environments
---

### Post by biocyberman on 2008-01-28
I am using gusty 7.10 gnome desktop with nautilus-cd-burner. I was able to burn cd/dvd before by using mouse clicks. But now when I try to burn iso file it shows this message even though I DID put blank cd/dvd into my drive:
 
**Reload a rewritable or blank disc**
Please replace the disc in the drive with a supported disc with at least 695.8 MiB<this is the iso file's size> free.  The following disc types are supported:
DVD+R DL, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+RW, CD-R, CD-RW

I remember when it was working, it can auto mount blank cd when I inserted but now it doesn't. 

cdrecord and dvd+rw tool are installed on my system already. 

Any clue please?

---

### Post by taurus on 2008-01-28
Have you tried using another burning app like brasero, gnomebaker, k3b, etc. to see if you can burn that ISO image?

---

### Post by biocyberman on 2008-01-29
I tried k3b, it failed neither. Error message said:
"cdrecord has no permission to open the device"
gnomebaker just said "failed" when I tried burning iso cd image. 

Is there something wrong with my LG SUPER MULTI CD+RW/DVD+RW DRIVE configuration?

This is the fstab line for my it: 
> 
/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec 0       0

symbolic link cd, cdrw, dvd, dvdrw in /dev/ all target to /dev/scd0

---

### Post by kpkeerthi on 2008-01-29
Found some [related discussions]("http://www.google.com/search?hl=en&q=cdrecord+has+no+permission+to+open+the+device+site%3Aubuntuforums.org")

Are you member of cdrom group? Type **groups** in a terminal to check. If not add yourself to cdrom group (see system -> preferences -> users & groups).

---

### Post by biocyberman on 2008-01-30
> **kpkeerthi said:**
> Found some [related discussions]("http://www.google.com/search?hl=en&q=cdrecord+has+no+permission+to+open+the+device+site%3Aubuntuforums.org")

Are you member of cdrom group? Type **groups** in a terminal to check. If not add yourself to cdrom group (see system -> preferences -> users & groups).

I check and I am in cdrom group, but cdrom group is not in the groups list so I added new group named cdrom. But that didn't help. I still got error and below is debug error message. I wasted 5 pieces of CD without getting the iso files burnt :(

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-H10N JL10 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H10N '
Revision       : 'JL10'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13032 kB/s 74x CD 9x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 8467 KB/s
Track 01: data   695 MB        
Total size:      799 MB (79:10.05) = 356254 sectors
Lout start:      799 MB (79:12/04) = 356254 sectors
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 3592
Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  695 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   34.678s
Average write speed 137.2x.
Fixating...
Fixating time:    0.004s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=48 -dao driveropts=burnfree -eject -data -tsize=356254s - 
```

---

### Post by biocyberman on 2008-01-31
<Bump>

---

### Post by biocyberman on 2008-01-31
Running gnomebaker from terminal showed me that required "mkisofs" package is not istalled. After installing that package, I managed to burn iso file by using gnomebaker. Why didn't it tell me it needs mkisofs at first place! :(

I am not sure, but chmod 777 of /dev/scd0, which is my optical drive, may also contributed to the working of gnomebaker.

However I still have problem with automount.

---

