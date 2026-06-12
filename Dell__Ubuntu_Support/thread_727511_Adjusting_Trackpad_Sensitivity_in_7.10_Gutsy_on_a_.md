---
title: "Adjusting Trackpad Sensitivity in 7.10 Gutsy on a 1420"
date: 2008-03-17
forum: Dell  Ubuntu Support
---

### Post by double051 on 2008-03-17
So, I really like using my trackpad under Windows and have the sensitivity maxed out but for whatever reason I cannot find out how to adjust the sensitivity in Gutsy. How do I do this?

The trackpad is 'Alps Pointing Device'. Thanks for your help.

---

### Post by fragos on 2008-03-17
The touchpad section in /etc/X11/xorg.conf is the place to go.  Here's mine.  The last 3 options are the ones that adjust sensitivity.  You can experiment until they work well for you.

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "0.7"
        Option      "AccelFactor" "0.0350"
EndSection

---

