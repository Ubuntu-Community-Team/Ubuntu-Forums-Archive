---
title: "DVD burner will not write to DVD"
date: 2008-08-06
forum: Desktop Environments
---

### Post by XtremeGamer99 on 2008-08-06
I dunno why. I've tried multiple times with three different DVD's (of the same type tho). Here's what I get in K3b:

```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.22-3-amd64
Devices
-----------------------
MAD DOG TF-DVDRW TSH652G MD00 (/dev/hdb, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdb obs=32k seek=0'
/dev/hdb: "Current Write Speed" is 20.5x1352KBps.
    1343488/4681422848 ( 0.0%) @0.0x, remaining 174:10 RBU 100.0% UBU   4.8%
    1343488/4681422848 ( 0.0%) @0.0x, remaining 406:24 RBU 100.0% UBU 100.0%
    1343488/4681422848 ( 0.0%) @0.0x, remaining 580:35 RBU 100.0% UBU 100.0%
    1343488/4681422848 ( 0.0%) @0.0x, remaining 754:45 RBU 100.0% UBU 100.0%
    1343488/4681422848 ( 0.0%) @0.0x, remaining 986:59 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=b80h failed with SK=4h/LOGICAL UNIT COMMUNICATION CRC ERROR (ULTRA-DMA/32)]: Input/output error
:-( write failed: Input/output error
/dev/hdb: flushing cache
/dev/hdb: updating RMA
/dev/hdb: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdb=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2285851 -use-the-force-luke=dummy -dvd-compat -speed=20 -use-the-force-luke=bufsize:32m 
```

I'm running Debian btw. I've also tried to burn it on my Windows partition, only to find it comes back with an error...

I've checked all the cables leading up to the DVD drive, and everything is secure in the case...

Any input?

---

### Post by phidia on 2008-08-06
There are a lot of hits googling > LOGICAL UNIT COMMUNICATION CRC ERROR (ULTRA-DMA/32) try [this post]("http://club.cdfreaks.com/f44/sony-dru-720a-logical-unit-communication-crc-error-ultra-dma-32-040803-a-133258/") on that particularly drive arrangement slave/master on the IDE bus.
Hope that helps.

---

