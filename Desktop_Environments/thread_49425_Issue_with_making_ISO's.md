---
title: "Issue with making ISO's"
date: 2005-07-16
forum: Desktop Environments
---

### Post by horsefactory on 2005-07-16
When I use the dd if=/dev/cdrom of=whatever.iso command, I get:

dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out

Now, the discs i'm trying to create an ISO from are perfectly readable and otherwise the drive itself performs excellently, I can burn ISO's properly, watch DVD movies etc. just not create ISO's.  I've tried a umount /dev/cdrom beforehand and bs=1024 at the end of the command as suggested in ubuntuguide.org and had no luck with that either.

The dvd-rw itself is a Lite-on SOHW-1673S, any help or alternative methods of making ISO's would be appreciated :)

---

### Post by z_pod on 2005-07-16
[QUOTE=horsefactory]When I use the dd if=/dev/cdrom of=whatever.iso command, I get:

dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out

Now, the discs i'm trying to create an ISO from are perfectly readable and otherwise the drive itself performs excellently, I can burn ISO's properly, watch DVD movies etc. just not create ISO's.  I've tried a umount /dev/cdrom beforehand and bs=1024 at the end of the command as suggested in ubuntuguide.org and had no luck with that either.

The dvd-rw itself is a Lite-on SOHW-1673S, any help or alternative methods of making ISO's would be appreciated :)[/QUOTE]

I usually use k3b to create isos from a boot/install cd....

As far as I know dd performs a physical dump of all the sectors of the the media to a image file, I'm not entirely sure it's the same thing as to create an iso image file.
Anyway, this is what I have (mine is a Samsung combo DVD-CDRW ide drive)

marco@ubuntu:~/Documents/tt$ sudo hdparm -d 1 /dev/cdrom
Password:

/dev/cdrom:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

marco@ubuntu:~/Documents/tt$ dd if=/dev/cdrom of=some.so bs=1k
466272+0 records in
466272+0 records out
477462528 bytes transferred in 234,086919 seconds (2039681 bytes/sec)

marco@ubuntu:~/Documents/tt$ ls -l some.so
-rw-r--r--  1 marco marco 477462528 2005-07-16 17:27 some.so

You may also try cdrecord or cdrdao (ie cdrdao copy --device /dev/cdrom).

This is what I have using k3b (Tools->CD->copy CD then check "Only create image")
-rw-r--r--  1 marco marco 477526016 2005-07-16 17:53 k3b_0.iso

It seems the 2 files are not the same......

Regards

---

