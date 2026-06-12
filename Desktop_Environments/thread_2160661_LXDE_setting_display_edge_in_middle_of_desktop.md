---
title: "LXDE setting display edge in middle of desktop"
date: 2013-07-07
forum: Desktop Environments
---

### Post by temporos on 2013-07-07
I'm using Lubuntu/LXDE on my old ASUS Eeepc 1005HA netbook. I have it connected to my TV via the VGA port. The netbook display shows as the DVI monitor (see attachment). Both displays work fine.

When the VGA monitor is connected, LXDE will still use the DVI monitor's resolution to maximize windows and for full-screen apps (see attachment). See how the SimCity window is "full-screen" only for the DVI display, leaving the right and bottom of the VGA monitor open? This happens for almost every window and app. Minimizing and re-maximizing the window will reset it to the DVI resolution.

Disabling the DVI monitor also disables the VGA monitor. I don't know why.

Can anyone help me on this? It's becoming really, ***really*** irritating. Is there a way to force LXDE to use the TV resolution when it's connected and the netbook resolution when it's not?

---

### Post by ohnonot on 2013-07-09
it is possible to have different resolutions for different screens.
i have an external monitor (VGA1) and i don't see why your TV should be treated dfifferently if it connects to the vga port.

install arandr and try with that.
your screens might be on top of each other, just drag them around. right-clicking allows you to change resolutions.
if you get a satisfactory solution you can save the settings to an executable shell script.
this shell script can be added to autostart (i don't remember exactly how lubuntu does this, but most probably there's a gui).

tell us how you get along!

---

