---
title: "Loading DVD or CD Freezes Computer"
date: 2006-07-17
forum: Desktop Environments
---

### Post by BenWilson on 2006-07-17
I just started Ubuntu after using Gentoo for a few years. It's great having (almost) everything working as expected. I'm having an odd situation, and I'm not quite sure what could be the culprit. The computer is an Averatec 3250H1. I am using 6.06, having installed it last week.

The problem is that whenever I insert a DVD or CD, the computer identifies the disc, then freezes. Only recourse seems to be a hard boot.

FWIW, the Averatec 3250 wireless card (Ralink-2500) originally froze the laptop whenever I tried to connect. The problem was resolved by putting "DisableIRQ" in xorg.conf, and "pollirq" in the kernel entry in grub.conf. Before then, I seem to recall the CDROM working.

Any ideas on where to start?

Regards,
Ben Wilson

---

### Post by x64Jimbo on 2006-07-17
You could try turning automount off. That would be the first thing I would do. I don't use it anyway ;)

---

### Post by BenWilson on 2006-07-21
The problem is larger. Trying to access the CD either via automount or straight mount locks the computer. Accessing the USB camera locks the computer. Before I interjected "pollirq" at boot, accessing the wireless card locked the computer.

Any ideas?

---

