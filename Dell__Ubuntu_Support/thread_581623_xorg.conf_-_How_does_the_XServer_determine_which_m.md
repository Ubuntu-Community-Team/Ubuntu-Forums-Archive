---
title: "xorg.conf - How does the XServer determine which monitor is which"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by Meson on 2007-10-19
I'm having one hell of a time getting my monitors to behave properly.  I see a lot of people pasting their entire xorg.conf files and asking for help, so rather than do that I'm going to try and pinpoint my particular problem.

I'm setting up two devices, two monitors, and two screens, but I realized there is no way of knowing if the monitor declarations in the file are going to the correct physical monitor.

Basically I'm setting up two nearly identical "Device" sections.  Except one I'm calling "nVidia GeForce FX Go5650 (Primary)" and the other "nVidia GeForce FX Go5650 (Secondary)".  In these sections I've also tried to play around with the Screen line and swap 0 and 1 between the two of them.

Now, for the monitors, I made an entry to go with my 2007WFP (Digital) and another one to go with my built in laptop monitor.

Then I created two screen entries to link the device and monitor entries...

It seems no matter which settings I try the monitors are not recognized correctly - possibly the opposite of how I want them.


My Setup:  
Dell Latitude D800 
GeForce FX Go5650 (using the nvidia driver)
Built in 15.4 Inch max res of 1280 x 800
Dell D/Port docking station
External Dell 2007WFP (Digital) max 1680x1050@60
Ubuntu 7.10

---

### Post by Meson on 2007-10-20
What should the ConnectedMonitor option be for the built in laptop monitor?  CRT, DFP, or even LFP?  I'm not sure about the support for the LFP option, I've only come across it in a few configuration files.

---

