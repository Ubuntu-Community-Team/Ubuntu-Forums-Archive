---
title: "Mobile 945 GM/GMS/GME and dual monitor problem"
date: 2010-02-17
forum: Desktop Environments
---

### Post by waelh on 2010-02-17
Hi!

I'm running Ubuntu 9.10 on a Toshiba Tablet PC with an integrated video chipset: Mobile 945 GM/GMS/GME, 943/940GML Express Integrated Graphics Control (as specified by lshw). Whenever I try to connect an external projector or screen my computer gives a black screen and/or freezes.

Please help me solve the problem.

Thanks,

Wael

---

### Post by warp99 on 2010-02-17
Plug in the monitor, than go to System > Preference > Display and press "Detect Monitor". If that's not working check your computer BIOS settings to see if your have the external monitor port enabled.

---

### Post by waelh on 2010-02-17
> **warp99 said:**
> Plug in the monitor, than go to System > Preference > Display and press "Detect Monitor". If that's not working check your computer BIOS settings to see if your have the external monitor port enabled.
Thanks for your help! I'm detecting the external screen but nothing is getting displayed on it, and then my computer freezes or a blackscreen shows up. I was able to prevent the freezing/blackscreen part by disabling visual effects, still no external output although its being detected

---

### Post by warp99 on 2010-02-17
Make sure the resolution of the external monitor matches the laptop. Highlight the laptop screen then try the "mirror" screen option so a common resolution can be used.

---

### Post by efflandt on 2010-02-17
I have a Toshiba laptop with same or similar video.

It works best if you boot with the projector already on (likewise for external monitor or HDTV).  Then it will pick a common resolution that both your built-in screen and projector can handle.  Otherwise if connecting the projector later, log out of X and log back in to have it recognized.  If you are doing a presentation and want to look at the tablet screen while mirroring that on the projector, that might be all you need to do.

However, with a VGA connection it will not necessarily chose an optimum resolution.  See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) to test other resolutions.

In my case I was trying to configure it for 1080p and cvt did not come up with proper timings for that resolution (it was horizonally scrunched and offset).  So I got info from my DVI to HDMI desktop /var/log/Xorg.0.log to come up with a working modeline for 1080p on the Toshiba's VGA.  Then I wrote a bash script using xrandr which sets up that mode for VGA, turns off laptop display, then switches VGA to that mode, and a desktop launcher that when double clicked, runs that script in a terminal.  Example (lines may be truncated unless you scroll over):

```
#!/bin/bash
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080_60.00
exit
```

---

