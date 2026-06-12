---
title: "Can't write DVD's in Jaunty (9.04)"
date: 2009-06-19
forum: General Help
---

### Post by linuxloon on 2009-06-19
Writing DVD's in Intrepid ( 8.10 ) worked fine. Same hardware after installing Jaunty 64bit burning DVD images fail. Brasero, K3b and cdrecord from the CLI all fail. Same symptoms. Burning starts and get's about 18Mb or so, not far and then fails. Here is the output from a burn of an image created in brasero ( though all iso burn's fail ) I have swapped the DVD burner. Same issues.

Output from cdrecord with -dummy on so I don't keep trashing DVD's .. same output w/o -dummy.

cdrecord -v -dummy brasero.iso 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-720A '
Revision       : 'JY03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1563904 = 1527 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
wodim: No such file or directory. Cannot open 'brasero.iso'.
makie@ubuntu:~$ cd /mnt/video
makie@ubuntu:/mnt/video$ cdrecord -v -dummy brasero.iso 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Looking for a DVD-R drive to store 4354.59 MiB...
Detected DVD-R drive: /dev/dvdrw
Using /dev/cdrom of unknown capabilities
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-720A '
Revision       : 'JY03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1563904 = 1527 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data  4354 MB        
Total size:     5000 MB (495:27.36) = 2229552 sectors
Lout start:     5001 MB (495:29/27) = 2229552 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 68944
Speed set to 22160 KB/s
Starting to write CD/DVD at speed  17.0 in dummy unknown mode for single session.
Last chance to quit, starting dummy write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Track 01:   18 of 4354 MB written (fifo  98%) [buf  99%]   6.7x.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 25 6B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 31.003s timeout 40s

write track data: error after 19617792 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:   64.148s
Average write speed  51.5x.
Min drive buffer fill was 99%
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.002s
wodim: fifo had 500 puts and 310 gets.
wodim: fifo was 0 times empty and 103 times full, min fill was 92%.

Same hardware works fine in 8.10 .. There seem to be a number of DVD/CD issues in Jaunty but I couldn't find this same issue when searching. Reading DVD's works fine. It's just writing that fail's.

Anyone have an Idea ?

---

### Post by 123456789123456789123456 on 2009-06-19
this problem seems to be a conflict with other programs, fix, go to add remove, remove both Brasero, and cd/dvd copy programs, after you remove them, go to synaptic, and completely remove Brasero, then back in add/remove, install Brasero

this should fix the problem.  I think that in earlier versions of Ubuntu, cd/dvd copy, and Brasero were two different programs, but now they are one in the same, cd/dvd copy is installed within Brasero.

I tried to reinstall both, and got the error, that the program Brasero can not be installed becasue it conflics with cd/dvd copy, and vice versa.

---

### Post by linuxloon on 2009-06-21
Tried that without any change. Tried removing any programs that have to do with DVD/CD writing, rebooting and the reinstalling just brasero but I'm getting the same error.

Have another system with 32bit 9.04 that is working ok. Had the slow write issue but disabling the brasero plug-ins fixed it. 

I'm almost thinking that it's a kernel issue/conflict with the hardware. I'm running out of ideas short of a full reload and I really don't want to do that and if it is a kernel issue re-installing won't help anyhow.

Other Ideas ?

---

### Post by linuxloon on 2009-07-09
As an update. I did a fresh install and it's working now. Something happened in the upgrade from 8.10 to 9.04 that got it confused.

---

