---
title: "How can I get higher resolutions on Dell 520"
date: 2010-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by valpd on 2010-03-23
I am running Ubuntu 9.04 on a Dell Latitude D520.

The highest resolution I can currently choose is 1024x768

cat /var/log/Xorg.0.log | grep -i uxa

returns

(WW) intel(0): DRI2 requires UXA

glxinfo | grep 'direct'

returns

get fences failed: -1
param: 6, val: 0
direct rendering: Yes

I have no idea what this means.  Is there a package (.deb) that I can install to give me higher resolutions?

---

### Post by coffeeaddict22 on 2010-03-26
Hi,
Depends on your graphics card.  Open a terminal and type in ```
lshw -C Display
``` and post the results back if you need a hand.
If you've got an ATI card, go into System/Administration/Hardware Drivers and enable the restricted driver for better effects.  The Nvidia cards also have a restricted driver, but the latest open driver is said to be pretty good.
Post back the output of ```
cat /etc/X11/xorg.conf
``` as well.  It should be pretty empty; Ubuntu is using HAL at present.

---

