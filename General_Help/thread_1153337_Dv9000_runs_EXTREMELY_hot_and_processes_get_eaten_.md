---
title: "Dv9000 runs EXTREMELY hot and processes get eaten up!  SOMEONE HELP PLEASE!!!"
date: 2009-05-08
forum: General Help
---

### Post by myk02k on 2009-05-08
Hey guys, I'm running into some serious problems with my dv9000 (amongst all the other ones I have experienced).  As of the last month, my computer has been getting hotter than it normally did even when on flat surfaces or in mid-air.  After running a few programs for over 2+ hours, I'd typically notice both my CPU and GPU temperatures spike to their threshold.  For instance, right now my GPU is at 210 degrees F and my CPU is at 207 degrees F.  If I put the hardware into moderate load or wait for a little while longer it may reach its threshold.  The spiked temperatures no longer trigger emergency shutdowns, which is alarming because I don't want any dangers of my battery blowing up.  

At the point where my processor and GPU reach their threshold, the processing usage spikes to 100% no matter what applications are in use.  I initially thought it may have been a Firefox memory leak, but have been recently noticing Xorg, compiz-fusion, nvidia-settings, totem, openoffice, etc slowly raise in process usage as the CPU/GPU reach near their temperature thresholds.  Programs will begin to not respond and I would normally be forced to close off absolutely everything (including compiz by way of a "metacity --replace" command) or shutdown and wait for a half an hour before resuming.

What can I do to resolve these issues?  Is there any way to manually manipulate/monitor fan useage?  Do I have a settings conflict or issue here?

My current specs are as follows:

Hewlett-Packard dv9000 Cheap Flawed Falling Apart Edition
(It features a self-destruct mode that arms once the warranty runs out...their reps surely know how to discourage and prevent repairing if it starts its work beforehand)
Intel T7200 Core 2 Duo 2.0 GHz
NVIDIA GeForce 7600 512 MB dedicated
2 GB DDR2 RAM
2x500 WD HDD

As for software I'm running Jaunty with the most recent Compiz and NVIDIA driver there is out there.  If any specifics are requested I will respond ASAP because I'm at a point of serious concern and inconvenience.  Thanks!

---

### Post by spiderbatdad on 2009-05-08
have you seen this thread? [http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
a little outdated, sorry, but possibly some useful information like boot options noapic irqpoll etc.

---

### Post by myk02k on 2009-05-08
Yes I did.  Are you suggesting that I missed something related to my issues in that thread or that I should post my issue there?

---

### Post by spiderbatdad on 2009-05-08
just checking in case there is something there to help. The thread is closed. Edited previous post to mention boot parameters.

---

