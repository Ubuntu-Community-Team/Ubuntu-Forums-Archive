---
title: "Emulators and Ram usage, best distro?"
date: 2012-10-29
forum: Emulators
---

### Post by PrinceOfJudah on 2012-10-29
I am running Ubuntu 12.04 right now, using the Lubuntu lightweight DE. unfortunately, firefox and chromium seem to eat enormous amounts of ram. I want to know if switching to Lubuntu 12.10 will make the ram usage reasonable, and if it is the best distro for running emulators.
I have 2 GB of DDR2 Ram at 667mhz
an e4500 core 2 duo, 2.2 Ghz
ATI Radeon 3870.

---

### Post by LillyDragon on 2012-11-22
2GB of Dual-Channel 2 RAM?! I'm shocked that you would even run into memory issues with that much, Linux generally has a better MMU than Windows. My desktop was just fine with half a gig of the same type of RAM on Hardy Heron, and my laptop's doing great on Xubuntu 12.04 with 3GB and six virtual desktops.

What edition of Ubuntu are you using, 64-bit or 32-bit? I don't want to jump to any drastic conclusions yet, but you could be triggering a bug in Firefox that's making it gobble RAM like crazy, or certain websites are total memory hogs. I don't think changing the distribution will affect either browser's memory usage, unless that distro has a bad port of Firefox, which I doubt since this is vanilla Ubuntu we're talking about here. =P

---

### Post by snowpine on 2012-11-22
Please take a look at this page and then post the results of **free -m** so we can discuss actual numbers rather than vague hypotheticals:

[http://linuxatemyram.com](http://linuxatemyram.com)

---

