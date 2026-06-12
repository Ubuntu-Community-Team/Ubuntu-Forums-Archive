---
title: "Slow disk access with newest kernel (2.6.12-10)"
date: 2005-12-07
forum: General Help
---

### Post by 5horizons on 2005-12-07
Hello,

I've noticed very slow disk access on my "run of the mill" IBM IDE deskstar drive (and Intel board) after upgrading to the newest ubuntu kernel.

Using the older kernel (2.6.12-9), and running "sudo hdparm -tT /dev/hda3" I get the following output:
/dev/hda3:
 Timing cached reads:   1344 MB in  2.00 seconds = 671.10 MB/sec
 Timing buffered disk reads:  126 MB in  3.03 seconds =  41.65 MB/sec

DMA is on for the old kernel, because running "sudo hdparm -d /dev/hda3" gives the result "using_dma    =  1 (on)".

However, if I run the same hdparm timing command with the newest kernel I get cached read speeds around 700 MB/sec, and buffered reads of about 4 MB/sec (very slow).

I have tried turning dma on for the drive, but it doesn't work.  It will just say "using_dma    =  0 (off)".

This appears to be a kernel thing.  For now I'll just run the older kernel.  Has anyone else seen this?  Should I report this as a bug?

Thanks

---

### Post by dabeej on 2005-12-08
[QUOTE=5horizons]Hello,

I've noticed very slow disk access on my "run of the mill" IBM IDE deskstar drive (and Intel board) after upgrading to the newest ubuntu kernel.

Using the older kernel (2.6.12-9), and running "sudo hdparm -tT /dev/hda3" I get the following output:
/dev/hda3:
 Timing cached reads:   1344 MB in  2.00 seconds = 671.10 MB/sec
 Timing buffered disk reads:  126 MB in  3.03 seconds =  41.65 MB/sec

DMA is on for the old kernel, because running "sudo hdparm -d /dev/hda3" gives the result "using_dma    =  1 (on)".

However, if I run the same hdparm timing command with the newest kernel I get cached read speeds around 700 MB/sec, and buffered reads of about 4 MB/sec (very slow).

I have tried turning dma on for the drive, but it doesn't work.  It will just say "using_dma    =  0 (off)".

This appears to be a kernel thing.  For now I'll just run the older kernel.  Has anyone else seen this?  Should I report this as a bug?

Thanks[/QUOTE]

Same here pal!

Bump!

---

### Post by schilcha on 2005-12-08
I've had similar problems with the cdrom. This [thread]("http://www.ubuntuforums.org/showthread.php?t=19519") did help.

---

