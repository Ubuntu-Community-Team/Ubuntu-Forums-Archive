---
title: "Lost all Drives - What the????"
date: 2006-02-11
forum: Desktop Environments
---

### Post by jccj7 on 2006-02-11
Hi,

Total Ubuntu newbie here....

I was in the process of getting my Ubuntu Breezy 5.10 system networked with my iMac and XP network.  I must have screwed something up while I was changing permissions and user functions because now none of my users have/show any drives mounted.  The CD-ROM, USB hard drive, and USB flash drives no longer show up or accessible.

Now after doing some searching, I tried to amend the fstab file, but no luck - all I could get was the CD-ROM drive to show up.  Here is my original fstab:

proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

I did change the CD from 'noauto' to 'auto' and 0it did show up.

So I need some ideas an0d su.ggestions on how to reclaim or 'auto-mount' my drives.

I'm still working on navigating and coding Linux, so please walk the dog with me.

Thanks in advance

jc

---

### Post by dcstar on 2006-02-11
[QUOTE=jccj7]Hi,

Total Ubuntu newbie here....

I was in the process of getting my Ubuntu Breezy 5.10 system networked with my iMac and XP network.  I must have screwed something up while I was changing permissions and user functions because now none of my users have/show any drives mounted.  The CD-ROM, USB hard drive, and USB flash drives no longer show up or accessible.

Now after doing some searching, I tried to amend the fstab file, but no luck - all I could get was the CD-ROM drive to show up.  Here is my original fstab:

proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

I did change the CD from 'noauto' to 'auto' and 0it did show up.

So I need some ideas an0d su.ggestions on how to reclaim or 'auto-mount' my drives.

I'm still working on navigating and coding Linux, so please walk the dog with me.

Thanks in advance

jc[/QUOTE]
Try removing and reinstalling the usbmount package, otherwise do a forum search for similar issues.

---

### Post by jccj7 on 2006-02-12
Thanks for the suggestion.  I tried several things like that based on suggestions to people having similar problems.  Yep, searching is great - but never found any working solutions.

Well, I ended up reinstalling Ubuntu and was able to get the network up and running quickly since I know all the in's and out's.

jc

---

