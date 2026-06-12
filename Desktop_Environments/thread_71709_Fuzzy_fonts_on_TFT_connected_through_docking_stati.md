---
title: "Fuzzy fonts on TFT connected through docking station"
date: 2005-10-04
forum: Desktop Environments
---

### Post by RikoW on 2005-10-04
Dear all,

I'm running Ubuntu on a Dell D600 with a ATI Radeon 9000 Mobile graphics chips set with 1024x768 resolution. Today, I connected the laptop through a port replicator with an external keyboard, mouse and 19'' TFT monitor.

Everything seems to be working just fine, except that the desktop fonts seems to be a bit fuzzier than on the internal LCD. Could that be a problem of the bigger resolution the TFT (in principle) has?

Can I adjust somehow an advanced font rendering, which makes the letters look sharper?

Thanks in advance,

               Riko

---

### Post by Pedro G. B. on 2005-10-04
Sure it could be... 19" LCDs generally have a native resolution of 1280x1024, so try changing your resolution to that while using the docking station.

Pedro.

---

### Post by RikoW on 2005-10-04
I assume, you mean changing the resolution of the laptop not of the TFT (at least, I didn't find a way to set the screen resolution down to 1024x768 ).
I know, that this is the max resolution of the laptop, but might be just limited by the LCD which is attached. If it is the graphics adapter which is the limiting device, i've lost.
However, I tried to add another screen section to the xorg.conf file:
```
        SubSection "Display"
Depth           24
Modes           "1280x1024"
EndSubSection

```
Hoping, either X would go into that resoltion by itself, if the attached monitor is capable of it, or at least I could set the resolution in the System -> Preferences ->Screen Resolution menue. But no such luck.
Is that the correct way of doing it?
Thanks,
Riko

---

### Post by seb_renaud on 2007-02-27
I have a similar problem: When my D600 when connected to the port replicator, I cannot change the screen resolution. Ubuntu installed on my laptop and configured a resolution of 1152x864 for the laptop screen. My docked screen ( LG Flatron 17in. ) does not seem to like that resolution ( it wants to have 1280x1024 ). I tried modifying xorg.conf as well, but while docked, the screen resolution is not changeable via the GUI. However, all the configurations I added are now available in the undocked state. I will try selecting the 1280x1024 resolution and make it the default while undocked and dock after... and post my info here.

---

