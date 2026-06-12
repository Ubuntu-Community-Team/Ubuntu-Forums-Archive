---
title: "Restoring On A Different System"
date: 2006-04-10
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-04-10
My normal rig has just gone and died (CPU overheated by looks of it), but before it did that, I had backed up everything as ISO images on a separate USB hard drive using Mondo. My problem is, how can I get about restoring that setup on this PC? I, annoyingly, can't get online with Ubuntu right now and have been looking for packages of Mondo Rescue to install, but they're all distro specific RPMs so far. 

Assuming I get Mondo on again, what's the steps involved in essentially overwriting this hard disk with the images from the USB disk?

---

### Post by taurus on 2006-04-10
If your backup is in ISO format, you can just mount it and copy whatever you want to your new system.  Assuming the name of your backup file is called backup.iso, open a terminal and do
```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop backup.iso /mnt/iso

```

---

### Post by Admiral Valdemar on 2006-04-10
Is there a code to get all the ISO files (at least 50 gigs worth all in 2 gig files) to automatically overwrite on to the system?

---

### Post by taurus on 2006-04-10
I guess it depends on how you did the backup!  If you backed everything from /, then you can mount your ISO on /mnt/iso.  Change to /mnt/iso and just copy everything from current directory to your new system.  However, doing THAT could cause some trouble later unless you have two identical PCs...

---

### Post by Admiral Valdemar on 2006-04-10
That's what got me, given the PC I'm forced to use now, while still a Pentium 4, is an older piece of kit and not the same specs. I assume you can correct any hardware inconsistencies with mod-probe or something or just select what files and settings you want to bring back. Or am I being too optimistic there?

---

### Post by taurus on 2006-04-10
Just take a step back for a minute.  You want to restore all the settings and services on your old PC using the new PC's (that went kaput) or do you just want to recovery your personal data in /home!

---

### Post by Admiral Valdemar on 2006-04-10
Well, I'd like to retain my programs, settings and data from the backup, since it's a pain to have a fresh install of Ubuntu and then install programs and set them up manually all over again.

---

### Post by taurus on 2006-04-10
What programs and settings are we talking here!  Maybe they won't take that long to setup on your new machine...

---

### Post by Admiral Valdemar on 2006-04-11
The point is that I'd like to have all the configurations already set, rather than go about installing everything all over, which would be redundant given I backed up from root. 

Mondo and Mindi won't install properly now, are there any dedicated Ubuntu packages? I'd use Synaptic, but given I can't get Ubuntu online right now...

---

### Post by taurus on 2006-04-11
I don't think you can just copy everything from one machine and dump it to another machine with different hardware and expect it to work out of a gate without some minor modifications!  If you do that on an identical hardware, perhaps but with a completely new system.  The most important directory you can backup is your /etc since it holds all the info about your system...

---

### Post by Admiral Valdemar on 2006-04-11
Yeah, that was pretty much what I wanted given the specs of both PCs were different anyway, so it'd only lead to hardware conflicts.

In anycase, thanks for the help all the same, but I managed to salvage my PC's CPU. Bent back some damaged pins and applied new thermal paste, now it not only works, it doesn't melt when under load!

---

