---
title: "Setting widescreen res in KDE for 2407WFP ?"
date: 2007-01-04
forum: Desktop Environments
---

### Post by FFred on 2007-01-04
Ok. I just upgraded my monitor from a CRT to a DELL 2407WFP LCD. I changed the xorg.conf file accordingly and everything works fine. Except in KDE which of course happens to be my main environment.

KDE insists on displaying at 1600×1200 (tested with a simple xwininfo on the root window) for some obscure reason. The native resolution for the screen is 1920×1200. 1600×1200 isn't even defined in the modeline :confused: 

When I kill the server and start it by itself (by just running X), it starts at the proper resolution. When I login through gdm and select the Gnome desktop, I get the proper resolution. When I select the KDE desktop, I get 1600×1200.

I tried using the KDE System settings panel to set the resolution but (of course) the Screen and Display applet crashes (in kcontrol_bridge_create_displayconfig, because 'NoneType' object has no attribute 'split' you know). I tried forcing a reinstall of the settings panel but it didn't change anything (as in it still crashes).

So I resorted to the trusted method of grepping around... doing variants of "grep 1600 | grep 1200" in all of $HOME/.kde didn't find anything, nor did it find anything in /etc/*/*

I suppose this weird resolution has to be set *somewhere* by KDE. However why it would set things differently from the X server baffles me. Or maybe it's so that it can switch resolutions on the fly and I haven't kept up with the times. Any way, if anyone knows where this is set (and how to change it), I'd be most grateful.

---

