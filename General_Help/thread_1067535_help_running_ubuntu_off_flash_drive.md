---
title: "help running ubuntu off flash drive"
date: 2009-02-11
forum: General Help
---

### Post by 1800yolk on 2009-02-11
I'm running ubuntu off of a flash drive, and installed it as if it were a hard drive (instead of System>Admin>Create a USB startup Disc). It works great on a few computers (aside from intermittent pauses, fairly light), but I'm having trouble getting it to work on every computer.

I think it's because when I install the OS, it detects what hardware I have and saves that info, and assumes that's all it will ever need. Is there a way to force Ubuntu to recheck all hardware on each boot? Or at least dump it on each shut down, that way it has to check the hardware environment and figure out what processor is needed and such?

Thank you! - Brian

This is with Ubuntu 8.10, Intrepid

---

### Post by dcstar on 2009-02-12
> **1800yolk said:**
> I'm running ubuntu off of a flash drive, and installed it as if it were a hard drive (instead of System>Admin>Create a USB startup Disc). It works great on a few computers (aside from intermittent pauses, fairly light), but I'm having trouble getting it to work on every computer.

I think it's because when I install the OS, it detects what hardware I have and saves that info, and assumes that's all it will ever need. Is there a way to force Ubuntu to recheck all hardware on each boot? Or at least dump it on each shut down, that way it has to check the hardware environment and figure out what processor is needed and such?

Thank you! - Brian

This is with Ubuntu 8.10, Intrepid

That's what installing onto a USB drive using the USB tool and a Live CD does.

Installing as a standard system gives you a standard system that does not waste time trying to auto detect things that it assumes will not change.

---

### Post by 1800yolk on 2009-02-12
I would totally do the live USB thing, but then I can't do the system updates :/

---

### Post by dcstar on 2009-02-12
> **1800yolk said:**
> I would totally do the live USB thing, but then I can't do the system updates :/

You make it a USB with persistence.

---

### Post by 1800yolk on 2009-02-12
Exactly, but the persistent installs all crash when doing the system updates. To my (limited) knowledge, there isn't a fix for that problem, so I went with a regular install. Still, thanks for the info

---

### Post by C.S.Cameron on 2009-02-12
You can use switchconf to select between several different xorg.conf files at boot depending on the computers hardware.
You can find it in the repositories.
It seems to work better with 8.04 than 8.10 when using restricted drivers.

---

