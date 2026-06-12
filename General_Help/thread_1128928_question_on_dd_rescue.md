---
title: "question on dd_rescue"
date: 2009-04-18
forum: General Help
---

### Post by Anfanglir on 2009-04-18
Hi
I have a question on dd_rescue.

I'm trying to fix an external harddrive with dd_rescue following the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=1056995&highlight=recover+harddrive&page=3](http://ubuntuforums.org/showthread.php?t=1056995&highlight=recover+harddrive&page=3)

The usb_disk was attached to my workstation at work when a network-technician installed a network version of XP, the local drives (including my personal usb drive) were wiped clean in the process...

Anyway, it's a 500 gb WD my passport connected through USB. I have run the command:
**sudo dd_rescue -b 10M /dev/sdc1 sdc1_image**
to create an image of the ereased drive on another harddisk. The program is chugging along with no errors reported so far, but it is really slow in progress. It's been running for 15 days now and has so far built 423 GB of the 500 GB image. The current rate is 100kB/s, it will take quit some time untill the last 80 GB are done...

The disk wasn't full, so I suspect that the last 80 GB are empty. Is it possible to terminate the dd_rescue process and still have a valid image to work on? My aim is to use testdisk to rebuild the partition table on that image (as described in the thread linked above). Any advice appreciated.

/ Anfanglir

---

### Post by danwood76 on 2009-04-18
Testdisk is the best tool to recover partitions, personally I dont back disks up when I use it, it only alters partition tables and the like.

Never used dd_rescue myself, I assume its a bit like dd (or uses dd) if thats the case you should have specified a different block size as that would have sped it up.

If it is like DD then I wouldnt interrupt it as you will end up with a dead disk image.

---

### Post by Anfanglir on 2009-04-19
OK, I leave it running 'till it finishes. 

Thanx / Anfanglir

---

