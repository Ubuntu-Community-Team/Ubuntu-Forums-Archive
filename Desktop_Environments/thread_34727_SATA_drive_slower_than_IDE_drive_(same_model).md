---
title: "SATA drive slower than IDE drive (same model)"
date: 2005-05-16
forum: Desktop Environments
---

### Post by Chareos on 2005-05-16
Hi all,

thanks to you all I'm tracking down every single problem on my brand-new Hoary system. I am, and will be, an Ubuntu user for a looong future :)


Today is SerialATA day.

I'm using a nForce4 mobo, Hoary amd64 with stock kernel.
My disks are:
Seagate Barracuda - 80GB - 2MB cache - IDE
Seagate Barracuda - 250GB - 8MB cache - SATA

As of now, SATA drive is slower, according to hdparm -tT
even in normal use I can see a noticeable performance drop when using the SATA drive (cpu climbs to performance with powernowd !)
Also, SATA drive don't accept DMA or access mode explicit adjustments.


Is there a way to solve ?
Thanks for any answer.

---

### Post by Chareos on 2005-05-16
Update:
compiled my own 2.6.11.9 kernel - better results with hdparm -tT

but also: HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device


and still can't explicit settings on SATA hd.

---

### Post by metasyntax on 2005-05-16
hdparm does not [yet?] support SATA drives fully because they are basically SCSI drives according to the kernel

---

### Post by Chareos on 2005-05-17
So I've to live with DMA disabled or is there another way ?
Is linux SATA support so late ?

---

### Post by metasyntax on 2005-05-17
I'm pretty sure that DMA is working fine on my drives... I can definatly capture video, rip cds and listen to music all at the same time.  I've got seagate & maxtor SATA drives, but YMMV and all that.  Just because you can't tweak or poll the settings with hdparm dosen't mean they are not being set... of course the inverse is true too.

I included my results for comparison (default hoary install): sda => 80g seagate 7200.7, sdb => 160g seagate 7200.7, sdc => 200g maxtor DiamondMax 9

I was listening to ogg's with muine, and capturing video from my miniDV camera at the same time I ran the tests, my CPU is in the 8%-12% range on an amd64 2800+ w/ 1Gig RAM.

As for linux being late to SATA, the devs are far more interested in correctness and data integrity than performance so that sometimes can explain things.

```
glenn@moria:~ $ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   2888 MB in  2.00 seconds = 1442.06 MB/sec
 Timing buffered disk reads:  164 MB in  3.01 seconds =  54.44 MB/sec

glenn@moria:~ $ sudo hdparm -Tt /dev/sdb
/dev/sdb:
 Timing cached reads:   2828 MB in  2.00 seconds = 1412.80 MB/sec
 Timing buffered disk reads:  164 MB in  3.01 seconds =  54.57 MB/sec

glenn@moria:~ $ sudo hdparm -Tt /dev/sdc
/dev/sdc:
 Timing cached reads:   2820 MB in  2.00 seconds = 1409.51 MB/sec
 Timing buffered disk reads:  150 MB in  3.03 seconds =  49.48 MB/sec

glenn@moria:~ $ uname -a
Linux moria 2.6.10-5-k7 #1 Tue Apr 5 12:56:05 UTC 2005 i686 GNU/Linux

```

Finally, to really test disks you should use something like [iozone](http://www.iozone.org/) witch should give you more indepth performance stats.

---

### Post by Chareos on 2005-05-18
I'm getting your numbers, really.
But my old Barracuda 2MB cache IDE ... gets higher.

If only I could get nvidia drivers wirking on my custom 2.6.11.9 ... that kernel gives me a SATA boost !

---

