---
title: "No Sound From EV1938 Sound Card"
date: 2006-01-03
forum: General Help
---

### Post by wsmoser2004 on 2006-01-03
I am brand new to Kubuntu, and I've just installed Kubuntu 5.10 with KDE 3.5 on a Gateway Solo 2150 Laptop.  Everything is working great so far except for the sound card, which is a Creative Labs Ectiva EV1938 (I've also seen the number CT4730 used).  I cannot get any sound to come from the laptop (neither speakers nor headphones).  Also, when logging into KDE, I get a message something like this: "/dev/dsp could not be initialized.  Output will continue, but using the null output device."  I have tried changing settings in alsamixer and KMix, and both mixers seem to be communicating with one another; when I change the volume in one it changes in the other.  However, I still get no sound.  I'm pretty sure nothing's muted.  It looks like alsa is loading the module "snd_ens1371", which I think is correct, but it's apparently not working.

I've searched for a solution to this problem everywhere, and no one seems to have a fix.  I'm finding out that apparently this sound card is notoriously difficult to make work.  I previously had FreeBSD installed on this laptop, and the sound also didn't work in there at first.  However, I eventually found a patch for a *.c file, and then sound worked after I recompiled the kernel.  However I can find no such patch for Kubuntu (and I also haven't figured out how to recompile the kernel yet!).

There might be a fairly simple fix for this...as I said, I'm new to Kubuntu and ALSA, so it may be a simple setting that I'm not seeing or a new driver I have to download.

Any suggestions?

---

