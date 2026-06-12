---
title: "External Monitor Unrecognized"
date: 2009-03-30
forum: Desktop Environments
---

### Post by Vengefulpickle on 2009-03-30
Recently (within the last few months), the external monitor that I have been using with my laptop has ceased to be recognized.

Some details:

The laptop is an Acer Aspire 5670. It has an ATI Mobility Radeon X1400. I'm currently running 8.10, and am not using the proprietary ATI drivers. The external monitor is plugged into a DVI port on the back of the laptop, and is a Nec 1735NXM.

In the past, I've been able to get the monitor to be recognized by adding to my xorg.conf in a separate section. However, I tried that yesterday using my old, pre-HAL xorg.conf, and had no luck.

As I mentioned before, I don't know precisely what I upgraded when the monitor stopped working, but it could have been upgrading to 8.10, it could have been an upgrade to HAL in 8.04, or it could have been an x11 upgrade.

When the monitor was working, it showed up on as DVI-0 when I ran xrandr. However, when I run it now, I see:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)

I can run any commands that would be helpful in diagnosing the problem.

Thanks in advance.

---

### Post by Vengefulpickle on 2009-03-31
One other thing I forgot to mention: I don't think it's a hardware issue (at least not an obvious one). I'm able to plug a different monitor into the DVI port, and use it successfully, and I'm able to plug the NEC into a different computer and have it recognized as well. So the issue is somewhere in the intersection of that monitor and Ubuntu.

---

