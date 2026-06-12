---
title: "Modules/Modprobe hanging issue:"
date: 2005-12-17
forum: General Help
---

### Post by klepto on 2005-12-17
I've been noticing that every few reboots linux would hang while either loading the modules or modprobe.. and i would have to do a hard reboot and wait a long time
due to the fsck'ing of the partition. 

How can I isolate and solve this problem?

---

### Post by mlomker on 2005-12-18
It's usually a piece of hardware that causes it (the driver might have a bug).  If there isn't an obvious indication of what is being loaded on the screen at the time of the hang then it might be tough.  

I'd start by disconnecting peripherals during bootup and see if that improves things (then you'll know that it was something that you unplugged).  I had a similar problem with the previous version of Knoppix--it would hang if I had USB devices plugged in but work fine if I plugged them in after bootup.  They fixed whatever issue that was in the latest version.

---

### Post by odrop on 2005-12-18
I've had the same problem every once and awhile also, but I find its usually my dirty'ish DVD drive trying to figure out whats in it while loading.  So check to see if it could be a dvd/cd drive trying to work, if it is, just eject it and it goes fine from there.

---

