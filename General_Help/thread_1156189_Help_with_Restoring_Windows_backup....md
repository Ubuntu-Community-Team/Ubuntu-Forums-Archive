---
title: "Help with Restoring Windows backup..."
date: 2009-05-11
forum: General Help
---

### Post by mikey5555 on 2009-05-11
Hello all, 
I am trying to assist someone with restoring a "tar" backup of Win XP Pro which was created by removing the hard drive from the XP machine, placing it in an external USB drive enclosure (necessary because drive would not boot and all recovery procedures failed to correct the boot problem), then connecting it to a PC running  Ubuntu 9.04, and backed up using the following bash script:
[b]#!/bin/bash          
SRCD="/media/disk-3/"
TGTD="/media/Video_Drive/Morris-BU/"
OF=morris-wade-$(date +%m%d%Y).tgz
tar cvpzf $TGTD$OF $SRCD[/b]

The XP drive was then wiped clean, formatted, and had XP Pro SP1 re-installed.  The objective is to restore the backup to this drive.  He  removed the XP drive, and put it in the external drive enclosure, connected via USB to the Ubuntu 9.04 machine, and restored the backup to the drive, using the following command: 
**tar xvpfz morris-wade-05082009.tgz -C /media/disk/** (the mount point changed from /media/disk-3 to /media/disk)

He ended up with the restore going to this directory structure: 
**c:/media/disk/...**
This put the entire backup into that directory instead of writing it to the "root" of "C:" drive.  

I am quite sure his (and my) lack of experience with this operation is the reason it got put in the wrong place.  I believe I have several alternatives I could try here:  
1:  Put the XP drive in an USB external enclosure, and restore from the Ubuntu 9.04 system to the external drive (this is what we tried and the results are what was explained above).
OR...
2:  Put the backup onto a different drive in an external enclosure and copy the backup file to it.  Then connect to the XP machine, boot with an Ubuntu Live CD, mount the drive, and attempt to restore to the XP drive using the this command:  **tar xvpfz morris-wade-05-08-2009.tgz -C /media/XP-Drive/** (I believe this is where I am dropping the ball, and causing the restore to be put into the directory "/media/Xp-Drive/" (or whatever I call the XP drive mount point).
Could someone advise me what the correct "syntax" for this command should be?  Or, possibly someone has a better way of restoring the backup file to the drive.  
Any pointers would be most appreciated....

Regards...
mikey5555

---

