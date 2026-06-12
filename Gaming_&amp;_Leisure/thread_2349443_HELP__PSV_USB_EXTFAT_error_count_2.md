---
title: "HELP:  PSV USB EXTFAT error count 2"
date: 2017-01-14
forum: Gaming &amp; Leisure
---

### Post by aljoriz on 2017-01-14
I am using PS VITA app called vita shell, it has a feature that uses USB to access the card but the card uses EXTFAT

Ubuntu Xenial has Extfat install from relan by default.  

I have tried the following codes:
> To mount exfat partition on Ubuntu, simply install the necessary packages:
[FONT=&quot]$ sudo apt-get install exfat-fuse exfat-utils[/FONT]

If you need to mount it from the command line, you could do
[FONT=Courier New]$ sudo mkdir /media/exfat[/FONT]
[FONT=Courier New]$ sudo mount -t exfat /dev/sdxx /media/exfat[/FONT]
where [FONT=Courier New]/dev/sdxx[/FONT] could be [FONT=Courier New]/dev/sda1[/FONT] or [FONT=Courier New]/dev/sda2[/FONT], or so on.

Upon mounting I get the error :
FUSE exfat 1.2.3
ERROR: unsupported FAT count: 2.

---

