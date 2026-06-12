---
title: "Replacing onboard soundcard"
date: 2008-12-15
forum: Desktop Environments
---

### Post by vexation on 2008-12-15
So.. I think I physically murdered my onboard audio, which is my fault for plugging stupid things into it and messing around with mixer levels too much. So, I replaced it with a PCI card (Audigy SE), which works fine.

The problem is, ALSA won't stop loading the onboard audio, even after disabling it in the system's BIOS.

What really annoys me is the fact that I even put snd-hda-audio in /etc/modprobe/blacklist, and the system STILL LOADS THE MODULE. Are things like "complete control over your hardware" now considered outmoded and quaint in the linux world? Are Linux devs taking lessons from Microsoft now? Is "ease of use" now so important that it trumps my authority over my own hardware? What's next? Ignoring Xorg.conf? Oh, wait you already do that, too.</rant>

Anyway, how do I force ALSA to either completely ignore the onboard audio, or to load the PCI card *first*, and load the onboard audio secondly and then do nothing with it?

OS is Ubuntu 8.10, fully patched/updated. Onboard audio is Intel HDA, replacement (PCI) is SB Audigy SE.

---

