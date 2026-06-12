---
title: "XServer lockup when starting firefox"
date: 2010-03-24
forum: Desktop Environments
---

### Post by surferX on 2010-03-24
I am new to ubuntu, but have been a linux user for the last 8 years. I switched my laptop a thinkpad t41 from gentoo to ubuntu... 

Its all installed but when I start firefox, before any window open the XServer freezes, and I can not access any of the VTs, so a reboot is required. I was going to try and have a look at how the Xserver is configured but I can't find /etc/X11/xorg.conf. 

Where does the installer put the Xserver configuration? Anyone had similar problem with firefox?

---

### Post by surferX on 2010-03-25
Bump

---

### Post by surferX on 2010-03-26
Found the answer, Xserver does not need an xorg.conf but to create one it was
#Xorg -configure

If I turn of all the effects under -->system--apperance--visual effects

firefox no longer crashes.

No just need to sorf the xserver problem and good to go

---

