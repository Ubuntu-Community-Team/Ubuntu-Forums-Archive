---
title: "k3b/cdrtools - unknown error 254"
date: 2010-10-12
forum: Desktop Environments
---

### Post by Kiesel on 2010-10-12
Hi, 
i just tried to burn a data dvd, but k3b says:

```
cdrecord returned unknown error code 254
```

the log gives me 
```
Devices
-----------------------
HL-DT-ST DVDRAM GSA-T40N JP01 (/dev/sr0, Cd-r, Cd-rw, Cd-rom, Dvd-rom, Dvd-r, Dvd-rw, Dvd-r DL, Dvd+r, Dvd+rw, Dvd+r DL) [Dvd-rom, Dvd-r sekvensiell, Dvd-r med två lager sekvensiell, Dvd-r med två lager och hoppmöjlighet, Dvd-ram, Dvd-rw begränsad överskrivning, Dvd-rw sekvensiell, Dvd+rw, Dvd+r, Dvd+r med två lager, Cd-rom, Cd-r, Cd-rw] [SAO, Track-at-once, Obehandlat, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Begränsad överskrivning, Lagerhopp] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2274218 (4657598464 bytes)

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-25-generic

Used versions
-----------------------
mkisofs: 3.0
cdrecord: 3.0

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: DMA resid 0 for 'read buffer', actual data is too short.
/usr/bin/cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 3.00 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-T40N '
Revision       : 'JP01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: DVD-R sequential recording
Profile: DVD-RAM 
Profile: DVD-R sequential recording (current)
Profile: DVD-R/DL sequential recording 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD+RW 
Profile: DVD+R 
Profile: DVD+R/DL 
Profile: DVD-ROM 
Profile: CD-R 
Profile: CD-RW 
Profile: CD-ROM 
Profile: Removable Disk 
Using generic SCSI-3/mmc-2 DVD-R/DVD-RW/DVD-RAM driver (mmc_dvd).
Driver flags   : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
Supported modes: PACKET SAO LAYER_JUMP
Drive buf size : 1114112 = 1088 KB
Drive pbuf size: 1966080 = 1920 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Data does not fit on current disk.
/usr/bin/cdrecord: Notice: -overburn is not expected to work with DVD/BD media.
/usr/bin/cdrecord: Notice: Overburning active. Trying to write more than the official disk capacity.
Track 01: data  4441 MB        
Total size:     4441 MB = 2274218 sectors
Current Secsize: 2048
Total power on  hours: 0
WARNING: Phys disk size 2298496 differs from rzone size 2274224! Prerecorded disk?
WARNING: Phys start: 196608 Phys end 2495103
Blocks total: 2274224 Blocks current: -16 Blocks remaining: -2274234
Reducing transfer size from 64512 to 32768 bytes.
Starting to write CD/DVD/BD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... /usr/bin/cdrecord: Input/output error. reserve_track_rzone: scsi sendcmd: no error
CDB:  53 00 00 00 00 00 22 B3 AA 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 53 00 00 0C 24 00 00 C0
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) error refers to command part, bit ptr 0 (not valid) field ptr 0
cmd finished after 0.002s timeout 200s
/usr/bin/cdrecord: Cannot open next track.
input buffer ready.
BURN-Free is ON.
Writing  time:    0.044s
Average write speed 999.0x.
Fixating...
Fixating time:    0.003s
/usr/bin/cdrecord: fifo had 128 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -overburn -data -tsize=2274218s -

mkisofs
-----------------------
/usr/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
2274218
/usr/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
Setting input-charset to 'UTF-8' from locale.
$DATA I WANT TO BURN
  0.02% done, estimate finish Tue Oct 12 16:06:21 2010
  0.04% done, estimate finish Tue Oct 12 16:06:21 2010
  0.07% done, estimate finish Tue Oct 12 16:06:21 2010
  0.09% done, estimate finish Tue Oct 12 16:06:21 2010

mkisofs calculate size command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -print-size -quiet -volid K3b-dataprojekt -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-kiesel/k3bV14656.tmp -rational-rock -hide-list /tmp/kde-kiesel/k3bv14656.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-kiesel/k3bw14656.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-kiesel/k3bE14656.tmp

mkisofs command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b-dataprojekt -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-kiesel/k3bA14656.tmp -rational-rock -hide-list /tmp/kde-kiesel/k3bF14656.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-kiesel/k3bz14656.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-kiesel/k3bG14656.tmp

```

Im remembering having similar issues a few month ago with wodim (which made me change to cdtools and solved the problem (at least for cds)), but now its there again. Does anybody have a clue on what to do?
Thank you very much! :)

P.S.: im running kubuntu 10.04

---

### Post by abyss88 on 2011-03-22
Hello. I was experiencing the same problem with k3b, brasero, gnomebaker. Always got a 254 error.

I solve this by:

```
sudo apt-get -y install wodim && sudo chmod 4755 /usr/bin/wodim
```

Hope this will help you to solve the problem, if not - write here :)

---

### Post by cybergrrl on 2011-04-04
it did not solve the problem for me, i still get the exact same error message as described above. i am using lucid lynx. thanks for any advice!

---

### Post by Kiesel on 2011-05-03
Hi,


sry for the late reply, but m laptop broke and after buing a new one i did not have the same problem (and url to this post) anymore.


Thank you for your answer :)
Kiesel

---

### Post by heitormsilva on 2011-11-07
This is your problem: [http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

---

### Post by Morpholinux on 2012-01-29
I got the same error
I changed the cd (Sony cd-r 700 Mb) for other just identical
Changed the speed from auto to 8x
Did a simulation
Everything ok
then Did it again for real
and Success

good day

by the way I am not running kubuntu, but ubuntu 11.10

---

