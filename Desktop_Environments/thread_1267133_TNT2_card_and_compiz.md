---
title: "TNT2 card and compiz"
date: 2009-09-15
forum: Desktop Environments
---

### Post by spkenny on 2009-09-15
I have an Nvidia TNT2 video card, trying to get it to work with compiz.  I let the automatic drivers install, and set everything up for compiz.  But when going to test compiz, nothing happens at all.  Double checking all the settings, I then wandered into the screen savers to look at those and found that not all of them were showing up in preview mode.  Made me think there was something wrong with the card.  I then put in a Xabre200-64 card, which is said to work seamlessly with linux based systems.  However upon installing this card, it put the resolution at its lowest.  With the TNT2 card I was at least getting 1024 x 768 I believe.  It was a really good resolution.  But upon re-installing the TNT2 card, now it will not return to high resolution no matter how many times I reinstall the driver.  Again I have always let xubuntu automatically install the Nvidia accelerated graphics driver legacy.  Do I need to get the driver directly from nvidia and install?  This all seems like its harder than it should be:(

---

### Post by spkenny on 2009-09-15
bump

---

### Post by spkenny on 2009-09-16
Update: It seems there is a driver download for the TNT2 card on the nvidia site. I downloaded the file, but am unable to figure out how to execute and install it. The specific instructions are:

Type "sh NVIDIA-Linux-x86-1.0-9639-pkg1.run" to install the driver, then edit your X config file as appropriate.

After keying that in, it cant seem to locate the file (even though its right there on my desktop). And I have no idea what an X config file even is. Somebody help me?

---

### Post by bobince on 2009-09-16
> After keying that in, it cant seem to locate the file

You need to go into the folder that contains the file, or you won't be able to run it. eg. ‘cd /home/username/Desktop’ if that's where you've saved it.

See [the manual](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.13/README/chapter-03.html) for how to set your xorg.conf.

But I think you are being massively optimistic trying to get compiz running on a TNT2. You know that's a ten-year-old card, yeah? It has the 3D performance of a broken potato.

---

