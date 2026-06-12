---
title: "fsck on boot (happens very often)"
date: 2009-03-11
forum: General Help
---

### Post by b00g1e on 2009-03-11
Every time i add a new hd or partition one i get the fsck failed error on boot. So i do a manual fsck and it "fixes" the problem everytime. Is there something im not doing when swapping one in or out, or is my boot drive failing? Maybe something else is causing the problems? 
thnx in advance

---

### Post by lensman3 on 2009-03-12
Are you "umount" the HD when you swap it out?  It sounds like you are not sync then a the files to the disk.  The sync command flush all writes to the disk and doesn't return until all write buffers are flushed.

Make sure you umount the disk.  

Try "/sbin/hdparm -Y /dev/sdxx" or the -y (lower case) option.  This put HD's into standby or sleep mode respecively.  Then remove the drive.  I think you need to spin the drive down before it is removed.

Also check "dmesg", the kernal stats reporting as the HD is umounted and spun down.  Dmesg will report the status.  Use the -f flag with fsck to force a partition check.

Hope this helps.

---

### Post by b00g1e on 2009-03-12
I'll give that a try next time, but do you think it will make a difference since i shut the computer down everytime

---

