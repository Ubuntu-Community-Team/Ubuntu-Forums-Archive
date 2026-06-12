---
title: "Configure Gnome sound subsystem?"
date: 2005-03-31
forum: Desktop Environments
---

### Post by cwaldbieser on 2005-03-31
Does anyone know how Gnome chooses what sound subsystem it uses for system sounds and whatnot?  When I upgraded to Hoary, I had some trouble initially getting sound to work.  I have managed to get XMMS to work by configuring it to use the ALSA library, and most of my games have sound if I run  esd and configure OpenAL to use SDL as the sound device, but I don't have any Gnome system sounds.

On my Kubuntu desktop, I had a similar problem, but I changed aRts to use the Open Sound System and device /dev/dsp1, and system sounds returned.  I am unable to determine if you can tell Gnome what sound system it is supposed to use, or what sound system it is actually using.

In case it makes a difference, I have two sound cards.  Both are Sound Blaster Live! cards, but one is a Dell OEMed card that doesn't work well with any Linux drivers I've ever used.

Anybody have any ideas?

---

### Post by ubuntu_demon on 2005-03-31
why not remove the DELL from your system then ?

use ESD in hoary (there are other threads about it .. next time do a search)

---

### Post by cwaldbieser on 2005-03-31
It's been a while since I cracked open the case, but I believe the built in card is somehow permanently attached.

I do have esd running (forgot to mention that in my previous post).  In fact, the OpenAL games I have won't play sound if it doesn't run-- but I have to configure them to use esd via SDL.  They won't use esd directly.

I have searched around concerning sound issues in the Ubuntu forums and on the Internet at large, but the information seems to be extensive and varied.  Some folks have luck with ALSA, others have no problems, still others must revert to OSS.

My thought was that since KDE let me switch from using esd to alsa to oss until I found one that worked, maybe Gnome would have such a configuration as well.

---

### Post by ubuntu_demon on 2005-04-01
If there's a soundcard integrated in your motherboard you should turn it off in your bios. If there's two soundcards inside pci/isa slots then you are able to physical remove one of them and should do so. This is the only help I can offer I'm afraid.

---

