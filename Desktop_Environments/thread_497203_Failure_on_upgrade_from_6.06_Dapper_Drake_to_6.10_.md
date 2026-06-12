---
title: "Failure on upgrade from 6.06 Dapper Drake to 6.10 Edgy Eft"
date: 2007-07-10
forum: Desktop Environments
---

### Post by gmillikan on 2007-07-10
I was upgrading using gksu "update-manager -c" and when the files were installing, my computer when into power saving mode and the screen powered off. Well, when I came back, the screen would not wake up no matter what I did!!  So I was forced to hard power cycle.

When I booted up, it went through GRUB just fine (dual boot) but after that, nothing.  The Linux kernal doesn't uncompress and boot.  The screen just sits there with a blinking cursor in the upper left hand corner of the screen.  No prompt, just a blinking cursor.

Is there any way to rescue this?  Can I reinstall Ubuntu without loosing all the data?

---

### Post by phidia on 2007-07-10
Do you have a livecd? e.g. ububtu, knoppix,something else? If you can boot from the livecd you can A) save your data to cd(s) or dvd and B) mount the install partition then chroot into it and in the chroot try to start and complete the update again. That method has worked for me on occasion. Hope that helps. 
Note: see man mount man chroot if you need to.

Added: You could also try the alternate ubuntu cd and the option from the start menu "Recover a broken system"
chances are though that will just drop you into a repair shell.

---

### Post by gmillikan on 2007-07-10
So I'm running the Ubuntu 7.04 disk and I can see in the File Browser "disk-1" which is the Linux partition.  I'm not totally clueless but "mount" and "chroot" are a bit out of my league to learn from scratch although to my credit, I read the full man pages on both and looked for examples on Google but that was fruitless.  I've tried to sign up for Canonical Global Support Services for USD $250 but of course nobody has called me and there's no phone number on their website.

The laptop has no CD/DVD burner unfortunatly. #@$%@#$
Tried to hook it up the Windows network and Ubuntu isn't recognizing it. #@$%#@$
Tried to hook up USB drive and I can read from it (formatted as NTFS) but I cannot write to it. @#$%
So I cannot get my files off - yet.

I'm happy to pay someone on PayPal or whatever to post an example of how to either recover all the data on the Linux partition and/or step in and fix the partially upgraded OS.

---

