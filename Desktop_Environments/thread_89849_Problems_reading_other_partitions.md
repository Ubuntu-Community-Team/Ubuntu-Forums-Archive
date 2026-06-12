---
title: "Problems reading other partitions"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Saku on 2005-11-13
Hi.

I recently got my own CD's of Ubuntu Breeze 5.10 sent to me and quickly changed from Windows XP Professional SP2 til Ubuntu.

Of course, having two harddrives, one on 80gig and one on 250gig, one doesn't want to lose much information so I saved everything to my NTFS partioned 250gig harddrive before I did anything.

I put in the Install CD and started installing Ubuntu, but when I was going to access my 250gig drive I couldn't find it at all.

Is there any way to read\write files and information to the NTFS drive whitout losing the current information that's stored on there?

(P.S: I heard somebody saying one could mount it by going into the Terminal and writing;
mount dev/hdd1/ /media/Windows (Where 'hdd1' is the name of my 250gig drive), is this a posebility?)

Thanks in advance. :)

---

### Post by Ampersand on 2005-11-13
The command would be
```
sudo mount -t ntfs /dev/hdd1 /media/Windows
```
as long as the 250Gb drive is the secondary slave. The Primary master is /dev/hda, primary slave is /dev/hdb, secondary master is /dev/hdc. You also need to make sure that /media/Windows exists first.

You can also access it by going to the Disks administration program (in System - Administration - Disks).

---

### Post by aysiu on 2005-11-13
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

