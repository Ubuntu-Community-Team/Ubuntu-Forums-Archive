---
title: "system backup"
date: 2005-11-06
forum: Desktop Environments
---

### Post by jrev on 2005-11-06
Hi all,

I am a Linux Ubuntu user and I would appreciate to learn about the proper backup to do before the hard disk failure.

What procedure and which application should be started before the crash, so that we can restore the full system after the crash on a new hard disk.

This procedure should be easy enough to be carried out by the average ubuntu user and reliable enough to be advised for all types of PC's

It should be quite interesting to make a wiki page on this topic

---

### Post by fannymites on 2005-11-06
I've tried using partimage to create an image of my ubuntu partition before re-arranging my partitions and it worked perfectly.
I just typed partimage --help and it told me everything I needed to do.

I've also tried using this method - [http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)
Again, it was easy to follow and I was able to restore my entire system with no problems.

---

### Post by adam.tropics on 2005-11-06
SBackup (Simple Backup), available via synaptic, is meant to be pretty good, and allows for scheduled backups to both local and remote drives or partitions, (via a nice gui), so could be very quickly restored with any one of a multitude of live cd distros available..... IN THEORY!!!

However, at the moment each time I try, even after a reboot, I get the error 


A backup run is initiated in the background. The process id is: 8878.


The process id changes, and each time I kill a process it reinvents itself!! Any ideas anyone? New to this, bear with me.....

---

### Post by bionnaki on 2005-11-06
[QUOTE=fannymites]
I've also tried using this method - [http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)
Again, it was easy to follow and I was able to restore my entire system with no problems.[/QUOTE]

I also recommend this - works great & is simple.
no need to install any application.

---

### Post by adam.tropics on 2005-11-06
Having tried a previous backup how to, I think that as a ntfs partition was mounted at the time it started to copy that as well. Anyway, due to a freeze, had to do hard reboot, and then tried sbackup. Each time i try that i get something like 

A backup run is initiated in the background. The process id is: 8959.

If i check the process id it is 'defunct'? but if i kill it, it restarts again. How can i stop it completely so i can use sbackup??

---

