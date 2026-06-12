---
title: "Twinview DPMS problem"
date: 2008-01-16
forum: Desktop Environments
---

### Post by Interstellar Overdrive on 2008-01-16
Hi all,

I'm using 2 Samsung 940NW monitors with an nVidia GeForce 8400 GS card (using the VGA output for 1 monitor and the DVI output with a VGA adapter for the second). Running Ubuntu 7.10

I used nvidia-setting to set separate X servers for each screen, which worked well except that one of the monitors kept going to sleep after a few minutes, whether I was using it or not. The only way to get it back on was to turn it off and on again. 

This is a really annoying 'feature' on these monitors, and happens under Windows as well if your power settings aren't right. I played with my power settings for a while, but couldn't fix the problem. Because it was just one of the monitors, I thought it might be a problem caused by having 2 X instances running (not sure if this is the right terminology here) so I changed to a twinview setup, but the problem didn't change. One of the monitors (always the same one) keeps going to sleep.

I'm guessing that it's related to my dpms settings, but I've tried everything I can think of to disable dpms. I'm new to linux so mostly I've just played with xset and tried removing all DPMS options from /etc/X11/xorg.conf. I've checked the BIOS setup, and the monitor options, but no luck there either.

I've also switched the outputs that the monitors are using, to try and narrow down the problem. But whether it's connected to the VGA or DVI output, it's always the same monitor going to sleep.

None of this has made any difference at all. I've searched these forums, I've tried google, but no luck so far. If anybody has any ideas I'd love to hear them.

Thanks in advance

---

