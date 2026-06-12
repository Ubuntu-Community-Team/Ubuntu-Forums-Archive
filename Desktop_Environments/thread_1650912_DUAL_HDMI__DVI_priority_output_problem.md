---
title: "DUAL HDMI / DVI priority output problem"
date: 2010-12-22
forum: Desktop Environments
---

### Post by complience on 2010-12-22
I'm having a real problem getting a non-mirrored dual desktop setup configured in ubuntu 10.10.

It is an ATI card with dual outputs one HDMI / one DVI using the ATI proprietary driver AMDCCLE.

I have this **working!** but only if the primary monitor/desktop is connected to the HDMI port and the secondary monitor is on the DVI, although AMDCCLE indentifys the HDMI monitor as screen 1 and DVI as screen 2.

The secondary monitor is primarly for media use so I need it for HDMI.

After setup if I connect the primary monitor back to the DVI port it shows the primary desktop, but as soon I connect the secondry HDMI output the primary screen dynamicly refreshes and shows only the background desktop (no panel or desktop icons) 

I am not sure if the screen/desktop identity is actually switching, resolution is changing or screen positioning is completely off wack.

Because it happens dynamically I think it might be related to Xrandr configuration.

I have tried configuration of my xorg.conf file correctly, but amdcccle rewrites it so it is of little help.

---

