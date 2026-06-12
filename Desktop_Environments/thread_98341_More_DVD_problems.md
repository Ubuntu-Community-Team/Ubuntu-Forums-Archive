---
title: "More DVD problems"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Leon The Cleaner on 2005-12-03
I'm a relative n00b to the world of Linux, moreso ubuntu.

I'm trying to get my system to play dvds but in xine and totem i get the following error msg:

Failed to find mount point for device /dev/hdd in /etc/fstab

I'm assuming i've got to edit fstab - how would i do this? And what do i enter to get it to see my dvd drive?

Any help Much appreciated.

Leon_The_Cleaner

---

### Post by aysiu on 2005-12-03
This is what my /etc/fstab looks like: ```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /windows        vfat    umask=000       0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0**
``` See how there are mount points for the CD-ROM drives? I guess yours is /dev/hdd. To edit your /etc/fstab, go to Applications > Accessories > Terminal and type in ```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

---

### Post by Leon The Cleaner on 2005-12-03
Ok that got me to fstab (thank you for that).

Ok this is what my fstab says - as far as i can tell there's nothing wrong with it. So as they say in the vernacular: WTF? what else could be causing my DVD woes?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

HELP!

Leon The Cleaner

---

### Post by Leon The Cleaner on 2005-12-05
... oddly i booted up my box this morning (2 days after an unsuccessful DeCSS re-install) and found my DVD drive recognizing the media in it. Yes I do a full shutdown every night. 

I don't know if this will continue to be the case - I'll keep you updated.

---

### Post by Leon The Cleaner on 2005-12-05
stupid thing did it again. this time i just went to try a different dvd.

```

Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount

```

---

### Post by CPUFreak91 on 2005-12-05
Hmm, i wonder if you can do the autoconfig for fstab without re-installing ubuntu (The magical fix for fixing windows... the best one is formating the partition and installing Linux)

---

### Post by bunty on 2005-12-06
[QUOTE=Leon The Cleaner]I'm a relative n00b to the world of Linux, moreso ubuntu.

I'm trying to get my system to play dvds but in xine and totem i get the following error msg:

Failed to find mount point for device /dev/hdd in /etc/fstab

I'm assuming i've got to edit fstab - how would i do this? And what do i enter to get it to see my dvd drive?

Any help Much appreciated.

Leon_The_Cleaner[/QUOTE]


What sort of DVDs? You dont mount audio CDs and (AFAIR) DVDs you just play them. I think xine is expecting something else. I know if I put an audio CD in my DVD burner it cant get it's poor little head around it and I get some dumb error.

---

### Post by Leon The Cleaner on 2005-12-07
I'm inserting a Movie DvD into a DvD-Rom. The problem seems to be inconsistent recognition that there's even something in the drive. IRONICALLY the drive will always recognize CD media placed in the same drive.

If i didn't know that the drive was fine I'd suspect that - but I put it into a windows box to test it and its fine.

Really very puzzled.

---

### Post by nalle on 2006-03-04
Did anyone come up with a solution to this problem?

I'm asking, because I think I have at least almost the same problem, with my dvd drive not recocnizing anything, but my cd drive working perfectly. The dvd drive has been working fine before, but now it just doesn't. I've played around with fstab, but it didn't help.

---

