---
title: "installing kubuntu 5.04 under vmware 4.5.2 (build 8848) not possible"
date: 2005-04-15
forum: Desktop Environments
---

### Post by dWLkR on 2005-04-15
hi all!

i wanted to test kbuntu 5.04 because as read and seen on several screenshots it´s very interessting to me :)

ok - my main system is currently winxp-sp1 on an AMD 2600XP / 512 meg / 64 meg nvidia geforce 4200

i´m using vmware 4.5.2 ([SIZE=1] [/SIZE]build 8848[SIZE=1] [/SIZE]) as written in the title above...

i created a virtual HDD with 4 gb space - i´ve set the file "kubuntu-5.04-install-i386.iso" as a virtual CD an reconfigured the boot-sequence for my virtual machine - ok after powering on the virtual machine it boots from "CD" - i can configure language stuff and LAN stuff - after that the HDD should be partitionated - but the install-routine reads some kind of error because no media was found :/

any ideas? (liveCD isn´t a solution for me ;))

---

### Post by dillweed on 2005-04-15
Have you set the mounted the kubuntu iso or have you made sure to specify which cdrom vmware should use for installation?  I've found that vmware doesn't always search correctly find the installation cd.  At any rate I've installed kubuntu and ubuntu using vmware and haven't any problems so far. 

Good Luck

---

### Post by dWLkR on 2005-04-16
[QUOTE=dillweed]Have you set the mounted the kubuntu iso or have you made sure to specify which cdrom vmware should use for installation?  I've found that vmware doesn't always search correctly find the installation cd.  At any rate I've installed kubuntu and ubuntu using vmware and haven't any problems so far. 

Good Luck[/QUOTE]
sorry i can´t get u here :/

could plz provide more information - maybe include some screenshots?
what vmware version r u using?

---

### Post by dWLkR on 2005-04-16
oh now i c...

no i can run the installation - as can be read in my first post... only the hdd detection fails when using vmware...

---

### Post by Rock on 2005-04-16
That's weird, I was able to install Kubuntu in vmware w/o any problems.

---

### Post by dWLkR on 2005-04-16
[QUOTE=Rock]That's weird, I was able to install Kubuntu in vmware w/o any problems.[/QUOTE]
could u pls write down your vmware settings and the version u r using?

i created a 4gb HDD drive...

---

### Post by dWLkR on 2005-04-16
ok my fault... i´ve now used an emulated IDE drive as HDD and seemingly it works :>

*installing* thx so far ^^

---

### Post by dillweed on 2005-04-16
Sorry I didn't help much your first post was vague to me, but that's just me.  My post was probably vague too. 

Anyways, on all the distros I've used the default of scsi emulated hd's don't seem to work and I always have to switch the hd to IDE.  That's just my experience.  

Glad you got it working.

---

### Post by jzietman on 2005-04-26
i have same problem but with normal ubuntu.  vmware 4.5.2 can't find the emulated ide hd during install. instalation works perfectly up till where the partitioner wants to format the hd before installing ubuntu

---

### Post by microchiroptera on 2005-08-03
Hello, I think it's the problem with debian.
I had the same problem as long as I tried to use SCSI-HDDs.
Use IDE-HDDs for your installation, then it will work.

Good luck!

---

### Post by helfor on 2005-08-04
Hi,

you have to load the module for the SCSI-HDDs manually.
If you get the partitioning error switch to the 2. console (ALT-F2) and try

modprobe BusLogic

---

