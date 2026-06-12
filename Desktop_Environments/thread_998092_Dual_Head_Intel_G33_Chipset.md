---
title: "Dual Head Intel G33 Chipset"
date: 2008-11-30
forum: Desktop Environments
---

### Post by tuxaddict on 2008-11-30
Hello Ubuntu Community,

I have an Intel G33 graphics controller and am trying to set up a dual monitor environment with ubuntu 8.10 Desktop and Intel X driver.

Ubuntu detects one monitor out-of-the box, but does not know anything about the other (identical) one (both monitors run at 1280x1024).

I did some research and made an xorg.conf as suggested in the intel documentation: [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) . The problem is that it just does not work. In console mode and with MS Windows, I have mirrored output on both monitors. But as soon as X starts, only one monitor is active and the other one goes black.

I tried to get some info with xrandr, and this actually reports that two monitors are connected, "VGA" and "TMDS". If I unplug the second (black" monitor", xrandr only reports one monitor, if I replug, both monitors are reported. It seems that the monitors are detected correctly by the video chipset.

After setting the virtual display size to 2560x1024 (2x1280) I also tried to set a correct monitor offset with xrand, e.g. I did:
xrandr --output VGA --auto --output TMDS-1 --right-of VGA

This actually "removes" the right border on the working monitor, so I can move the mousecursor to the other screen, but the second monitor remains black so I don't see anything. "Xrandr -q" reports correct resolutions, offsets and monitor connections, xorg.0.log also looks alright and does not show errors.

Can someone help me with this issue? Is this a known problem/limitation with the intel graphics driver? What can I do to fix this?

Thanks in advance for your help!

Rgds,

Ta.

---

