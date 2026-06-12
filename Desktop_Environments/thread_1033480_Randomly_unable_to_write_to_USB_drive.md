---
title: "Randomly unable to write to USB drive"
date: 2009-01-07
forum: Desktop Environments
---

### Post by alanh on 2009-01-07
I'm using 8.10. For about 12 months I have worked primarily from a USB drive, between Ubuntu and XP.  Since I "upgraded" from Gutsy to Ibex (my biggest mistake), I have had problems where the drive will randomly decide to be read-only, sometimes while navigating the drive contents (ie: during the same mount, it will suddenly decide to be read-only). It works perfectly fine with XP.

(1) The Nautilus properties dialog shows me as the owner with RW permissions 

(2) $ ls -l gives the following output:

drwx------  8 alan root  4096 2006-08-11 22:37 Application data
-rwx------  1 alan root   170 2006-11-18 20:37 Autorun.inf
-rwx------  1 alan root  3212 2008-03-12 18:55 BOOTEX.LOG
drwx------ 12 alan root  4096 2009-01-07 11:44 Documents
drwx------  2 alan root  4096 2006-08-21 13:18 FOUND.000
drwx------  2 alan root  4096 2007-07-18 08:42 FOUND.001
dr-x------ 20 alan root  4096 2007-03-05 20:21 PortableApps
drwx------ 15 alan root  4096 2006-08-11 22:37 Program Files
-rwx------  1 alan root 52476 2006-11-18 20:00 StartPortableApps.exe
-rwx------  1 alan root    11 2007-03-07 08:49 SyncToyDirectoryId.txt
drwx------ 11 alan root  4096 2006-08-11 23:28 Utilities
-rwx------  1 alan root  2710 2006-08-17 10:38 U.xml

(3) $ mount gives the following output:

/dev/sdb on /media/TRAVELDRIVE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

(4) I've tried remounting and cleanly unmounting the drive in XP

This is becoming a major pain and will end up being a real barrier to working in Ubuntu, if I can't get it fixed.  

Can anyone please help?

Alan

---

### Post by decoherence on 2009-01-07
How do you tell that it has become read only? Specific error messages are helpful.

---

### Post by alanh on 2009-01-07
Copied from error dialog box:

-------------------------------------------------------------------------------------------------------------
Error while copying "Distributed engine control - NASA - 2007.pdf".

There was an error copying the file into /media/TRAVELDRIVE/Documents/GaN/Articles/Technology/Device & circuit technology/RF switches.

More details:

Error opening file '/media/TRAVELDRIVE/Documents/GaN/Articles/Technology/Device & circuit technology/RF switches/Distributed engine control - NASA - 2007.pdf': Read-only file system
----------------------------------------------------------------------------------------------------------

---

### Post by skullmunky on 2009-01-07
run the command 'dmesg' in the terminal after you get this error and post the output.  Also, in Windows, run a full disk check on the drive and check the options to test for bad blocks.  I don't know if this'll come up with anything, but it'll rule out problems with the drive.

I've had problems like that before, sudden random read-only access on drives, particularly when copying, and sometimes it turns out that what's going on is that there's a small disk error, like a bad block, and Linux quickly unmounts and remounts the drive read-only behind the scenes to prevent file corruption.  In the dmesg output, look for anything like an "I/O error" and messages about "remounting read only".

---

### Post by Nerdriot on 2009-01-08
What skullmunky said. That happens to me occasionally after adding and removing a lot of things from flash drives and such. Eventually, it just seems to "give out", and I end up backing everything up and formatting the flash drive and starting over.

Small hassle, but nothing major.

---

### Post by rwigle on 2009-01-08
Happened to me and I think you are right.... The following link might help

[https://help.ubuntu.com/community/Mount/USB#Device%20become%20suddenly%20read%20only](https://help.ubuntu.com/community/Mount/USB#Device%20become%20suddenly%20read%20only)

---

### Post by alanh on 2009-01-08
Hey guys, many thanks for your suggestions - they were dead-on right.  Last night I ran a check on the drive through GPARTED (I'm really not a command line person) and it showed disk errors.  I made a back-up of the files, reformatted the drive, reloaded the files and everything is fine now.

Many thanks again,

Alan

---

### Post by alanh on 2009-01-08
Hey guys, many thanks for your suggestions - they were dead-on right.  Last night I ran a check on the drive through GPARTED (I'm really not a command line person) and it showed disk errors.  I made a back-up of the files, reformatted the drive, reloaded the files and everything is fine now.

Many thanks again,

Alan

---

### Post by alanh on 2009-01-09
I wanted to thank you guys but, for some reason, my replies below didn't bump the post.  Anyway, thanks again.

---

### Post by Nerdriot on 2009-01-09
No problem at all :) Glad we could help.

---

