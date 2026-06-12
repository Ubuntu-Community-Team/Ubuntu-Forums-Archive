---
title: "TNT2 Won't Use Xgl?"
date: 2007-12-31
forum: Desktop Effects &amp; Customization
---

### Post by GoldenKevin on 2007-12-31
Recently, I installed a fresh copy of Ubuntu Gutsy Gibbon. First I had to install glx for my NVIDIA TNT2 card, which after much struggling and reformating, I finally got it to work.  However, now I want to use Compiz Fusion for desktop effects, but even with glx enabled, it will not change.  So, then I typed "compiz" in the command line and it said:

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0028 (rev 15) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present
aborting and using fallback: /usr/bin/metacity

So, I'm guessing I had to get Xgl, but when I downloaded the package "xserver-xgl" from Synaptic Package Manager, it looked as though it installed alright, and I guessed I had to restart my computer.  However, when I logged onto Ubuntu using either GNOME or xclient, it had a black cursor in the shape of an "X", and these weird things started happening on screen, like it kept flashing black and orange.  Anyone know what's going on here?  Is the TNT2 card not supported or something?  I had to go to Failsafe GNOME just to get my computer into a usable state, then unistall xserver-xgl so I could boot my computer properly

---

### Post by FuturePilot on 2008-01-01
For Nvidia cards you do not need XGL. Just make sure the restricted driver is installed. System>Administration>Restricted Driver Manager. However unfortunately I do not think your card can support Compiz.

---

### Post by GoldenKevin on 2008-01-01
Yeah, well, I installed the restricted drivers, and I double-checked to make sure it said it was enabled and it was checked.  If it changes anything by the way, my card is a nvidia legacy card.

---

