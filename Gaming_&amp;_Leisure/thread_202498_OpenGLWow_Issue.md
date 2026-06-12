---
title: "OpenGL/Wow Issue"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by SquatcHman on 2006-06-23
I've been wrestling with this problem for more than a few days now.  I have no problem running the World of Warcraft client using wine.  The interface, chat, and addons all work quite well(copying the client from a windows installation).  All 3d graphics are not rendered at all however.  Starting the game from cedega kicks out with an "unable to start 3d acceleration" error.  

glxinfo reports that direct rendering is enabled.
OpenGL vendor string:  NVIDIA Corporation
OpenGL renderer string:  GeForce Go 7800 GTX/PCI/SSE2
OpenGL version string:  2.0.2 NVIDIA 87.62

glxgears displays just fine.
planet penguin played well.

My xorg.conf file shows:
> Section "Device"
     Identifier   "Nvidia Corporation NVIDIA Default Card"
     Driver    "nvidia"
EndSection


I'm not sure where the problem is.  While tuxracer worked just fine, the only other game I tried was City of Heroes, which worked swimmingly with cedega.  I use Automatix to install the nvidia-glx package, and when I do that I am unable to change my desktop resolution from 1920x1200.  While that is an odd note, it does nag at my mind.

Any ideas?

---

### Post by Scunizi on 2006-06-23
Nvidia's latest driver is in Synaptic.  That's what I used to install it.  Then into xorg.conf to comment out the DRI line.  Although I haven't played with WoW, you might try reinstalling the driver from Synaptic.  Wait for a while for reply's to my post though. I'm not sure if Automatix does something that will mess with a Synaptic install.  Of course you could always try it and if things get borked ... well you'll have a NEW adventure.  By the way, if you're running XLG and compiz that might be your issue.  Full screen games don't like xlg.

---

### Post by SquatcHman on 2006-06-23
No xgl... just good ole gnome.

---

