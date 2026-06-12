---
title: "DVD recording problems"
date: 2006-10-06
forum: Desktop Environments
---

### Post by kabads on 2006-10-06
I'm getting problems burning DVDs (it was working less than a week ago). 

I've not found any good diagnostics, apart from the output from k3b (although I did try gnomebaker first, which had similar output). 

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
DVDRW IDE H16X B02P (/dev/hdd, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
WARNING: /dev/hdd already carries isofs!
About to execute 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
/dev/hdd: restarting DVD+RW format...
/dev/hdd: "Current Write Speed" is 4.1x1385KBps.
         0/1004589056 ( 0.0%) @0x, remaining ??:??
         0/1004589056 ( 0.0%) @0x, remaining ??:??
         0/1004589056 ( 0.0%) @0x, remaining ??:??
         0/1004589056 ( 0.0%) @0x, remaining ??:??
         0/1004589056 ( 0.0%) @0x, remaining ??:??
         0/1004589056 ( 0.0%) @0x, remaining ??:??
:-[ WRITE@LBA=0h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:490522 -dvd-compat -speed=4 


Does anyone have a clue about what might be going wrong here? It doesn't seem to be a front-end problem (k3b, gnomebaker) but could possibly be something to do with the latest cdrecord (althought that came in more than a week ago). 

TIA
Adam

---

