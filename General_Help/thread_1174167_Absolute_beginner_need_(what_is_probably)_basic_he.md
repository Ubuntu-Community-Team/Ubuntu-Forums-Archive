---
title: "Absolute beginner need (what is probably) basic help"
date: 2009-05-30
forum: General Help
---

### Post by rslater on 2009-05-30
Hi all, I am a complete newbie to Ubuntu, so please go easy on me...
I am running a P4 desktop with 2 hard drives.  XP Pro is installed in the first and the 2nd hard drive is partitioned into 2.  A work area for files and a Ubuntu installation.  I have dual boot setup.

I was using ubuntu 8, but decided to update to Ubuntu 9.04, so I downloaded the ISO and installed from that.  The install seemed to go OK and all seems to work, apart from I cannot download any updates or packages.  This seems to be due to the / file being full, /media seems full, /var/lib nearly full and the /home/"user"/.mozilla/firefox/qglqo77p.default files all full at 100%.

I got this information from Disk Usage Analyser.  I can only assume that enough file size was allocated during the install.

As I have had enough of windows crashes and have comited to Ubuntu, I was impressed by ver 8, but now need some of the features of 9.  I really need to get this working so any help is greatlt appreciated.

---

### Post by trench.me on 2009-05-30
You might read through the following thread and see if it helps at all.

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by michy99 on 2009-05-30
How big is your Ubuntu partition?

---

### Post by rslater on 2009-05-30
As a newbie, how can I confirm the size?

---

### Post by rslater on 2009-05-30
Doh...

/dev/sda1  fuseblk    128G   59G   70G  46% /media/HARD DISK 1
/dev/sda5  fuseblk    105G   63G   43G  60% /media/HARD DISK 2
/dev/sdb1  fuseblk    231G   61G  171G  27% /media/HARD DISK 3
/dev/sdb5     ext3    2.3G  2.2G   30M  99% /
Filesystem    Type    Size  Used Avail Use% Mounted on
lrm          tmpfs    502M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1.0M   16K 1008K   2% /tmp
tmpfs        tmpfs    502M     0  502M   0% /lib/init/rw
tmpfs        tmpfs    502M   92K  502M   1% /dev/shm
udev         tmpfs    502M  188K  502M   1% /dev
varlock      tmpfs    502M     0  502M   0% /var/lock
varrun       tmpfs    502M  104K  502M   1% /var/run


so I can see dev5/sdb5 is full, how do I cure this?

---

### Post by buntunub on 2009-05-30
When you installed 9.04, did you select the "use remaining free space" option?

---

### Post by rslater on 2009-05-30
I cannot honestly remember, it was the early hours of this morning.  Can the files size be adjusted?

---

### Post by rslater on 2009-05-30
Gave up in the end, did a reinstall, all seems ok this time

---

