---
title: "Aptitude auto-remove all packages, killing system"
date: 2007-12-31
forum: Desktop Environments
---

### Post by GMU_ninja on 2007-12-31
Background info:
System:  Ubuntu 7.04 on AMD 64 processor with 4 SATA drives in RAID, plus 1 IDE for system.
System is setup as a file server for my backups.  Only installed base system, plus LAMP server.  After install I added a few other packages I wanted (Samba, etc.).  System went on working untouched for several months.

Problem details:
Recently I started using the system more.  I updated all the packages using aptitude, no problem.  I added a couple packages, changed the configuration a little, and rebooted.  Still no problem.  I added Webmin.  The next time I use aptitude, it wants to uninstall all of my packages (436MB of packages) because it thinks they aren't being used (in category "Packages to be Removed because they are no longer used").

After some talk on the IRC channel, someone suggested that after everything is removed, it will be added back again.  I let aptitude do it's thing and it destroys my system.  The only package it couldn't remove was sudo.  The sytem will no longer boot up, and using aptitude is not possible.

Anyone know what happened?  I am already attempting to restore the system, but I would like to know the cause of the problem so that it doesn't happen again.  If I should grab any log files, let me know which ones (and exact location).

---

### Post by jamaisvu on 2008-01-01
[FONT=Franklin Gothic Medium]I don't know what happened to you, but (sorry if this is stating the obvious) if you don't have your /home/ directory on its own partition (or already backed up), you should try reading it from a live CD (Knoppix might be better than Ubuntu for this) and copying any valuable data to another medium (e.g. floppies, another HDD, a USB flash thingy etc) *before* trying to reinstall an OS.[/FONT]

---

### Post by bapoumba on 2008-01-01
To the OP: aptitude uses its own log file for its actions. This is why aptitude and apt-get/Synaptic should not be used alternatively. I use aptitude only, and not apt-get/Synaptic. My guess is that aptitude removed all that it did not know that was installed by you.

Do you have a separate /home partition? Can you boot in recovery mode from the grub menu (I doubt so but hmm.)?

---

### Post by steveneddy on 2008-01-01
> **bapoumba said:**
> To the OP: aptitude uses its own log file for its actions. This is why aptitude and apt-get/Synaptic should not be used alternatively. I use aptitude only, and not apt-get/Synaptic. My guess is that aptitude removed all that it did not know that was installed by you.

Do you have a separate /home partition? Can you boot in recovery mode from the grub menu (I doubt so but hmm.)?

Hmmm - interesting. I didn't know this about aptitude.

This would explain a recent reinstall because I used apptitude in previously installing and trying to remove it by an alternate method.

---

### Post by bapoumba on 2008-01-01
> **steveneddy said:**
> Hmmm - interesting. I didn't know this about aptitude.

This would explain a recent reinstall because I used apptitude in previously installing and trying to remove it by an alternate method.
Yes, that's one tricky point. I've used aptitude after a fresh install (a long while back..) when the autoremove option was not available for apt-get. At this time, aptitude used to better handle dependencies, -recommends etc. Now the gap has vanished between the two, but I'm used to it and still use it exclusively.

Unless for a special purpose, they should not be used on the same install. I once removed a package with apt-get on purpose, to keep ubuntu-desktop installed (although broken for a while ;)).

---

### Post by GMU_ninja on 2008-01-01
> **bapoumba said:**
> To the OP: aptitude uses its own log file for its actions. This is why aptitude and apt-get/Synaptic should not be used alternatively. I use aptitude only, and not apt-get/Synaptic. My guess is that aptitude removed all that it did not know that was installed by you.

Do you have a separate /home partition? Can you boot in recovery mode from the grub menu (I doubt so but hmm.)?

I do have a seperate /home partition, and I am currently reinstalling the base system.  My issue was not data recovery (I can do that on my own), my issue was why Aptitude so dumbly decided to destroy my system.  I am not exaggerating when I say it removed every package and every program from my system.  After it was done, it would only boot into the basic (initramfs) prompt and I could do nothing!

I am considering submitting a bug, but I guess it would be in the aptitude package rather than any Ubuntu package.

---

### Post by bapoumba on 2008-01-02
> **GMU_ninja said:**
> I do have a seperate /home partition, and I am currently reinstalling the base system.  My issue was not data recovery (I can do that on my own), my issue was why Aptitude so dumbly decided to destroy my system.  I am not exaggerating when I say it removed every package and every program from my system.  After it was done, it would only boot into the basic (initramfs) prompt and I could do nothing!

I am considering submitting a bug, but I guess it would be in the aptitude package rather than any Ubuntu package.
It's a feature, GMU_ninja, not a bug ;)
Packages managers can do very powerful things. And you _were prompted_ to apply changes, with all the packages listed to be removed, and you _did say yes_. Every package manager, Synaptic, apt-get, aptitude (and may be dselect, but I do not use it) _always_ ask for confirmation and _always_ does what the user ask it to do.

This is why I asked for the separate /home partition, makes things easier when it comes to reinstalling (or upgrading to the next release with a fresh install). 
I'm very sorry this happened to you, you did not get a very good advice to start with. At least, now you know. And please do not feel bad, this is how I got interested into package managers myself :)
(But I did not hit the Yes button, I looked around).

---

