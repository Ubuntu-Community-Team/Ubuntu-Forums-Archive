---
title: "Touchpad too sensitive"
date: 2009-02-18
forum: Desktop Environments
---

### Post by erbedo on 2009-02-18
Hi
    I've just installed Kubunt, and the touchpad was to sensistive from the beginning. I can barely move from one window to another and it clicks. Usually a normal movement of about 10 cm equals to 4/5 clicks.
I looked into the xorg.conf, but there was anything about the touchpad. So I installed gsynaptycs, and after setting all the options to "Low Sensitivness", the problem is still here.
So i looked into the xorg.conf and wrote that:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "auto-dev"
        Option          "Emulate3Buttons"       "on"
        Option          "SHMConfig"             "on"
        Option          "FingerLow"             "24"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "180"
        Option          "MinTapTime"            "110"
        Option          "ClickTime"             "0"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "50"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.50"
        Option          "MaxSpeed"              "1.00"
        Option          "AccelFactor"           "0.15"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "3"
        Option          "VertEdgeScroll"        "on"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

It seems that tapping hard the touchpad and then moving (like a click) doesn't do a click, insted tapping it easy like when you want to drag something, did a click.
After that, the vertical scroll doesn't work, but maybe that's another problem I don't know.

Any hint??

Thanks

---

