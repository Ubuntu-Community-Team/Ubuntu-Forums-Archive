---
title: "Trcdrecord: Cannot load media"
date: 2006-08-22
forum: Desktop Environments
---

### Post by ridshack on 2006-08-22
I can mount and read CDs but cant seem to write any. Ive used the gnome cd/dvd writer and gnomebaker but the media isnt identified as writable. BTW when I insert a blank disk it does mount and show on the desktop. Here is the  log from gnomebake. Also I have tried two different brands of CDRW and I was able to burn in windows before wiping and loading Ubuntu a few days ago. Ive tried burning sudo with same results. Any ideas?

Thanks


```

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TEAC    '
Identifikation : 'DW-224E-A       '
Revision       : 'A.2F'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0008
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 
Profile: 0x0008 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
Drive buf size : 1421312 = 1388 KB
FIFO size      : 4194304 = 4096 KB
Trcdrecord: Cannot load media.
```

---

### Post by atomkarinca on 2006-08-22
you can try nerolinux: [http://www.nero.com/eng/nerolinux-prog.html](http://www.nero.com/eng/nerolinux-prog.html)

---

