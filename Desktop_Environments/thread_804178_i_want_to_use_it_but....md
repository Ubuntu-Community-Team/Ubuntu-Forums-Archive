---
title: "i want to use it but..."
date: 2008-05-22
forum: Desktop Environments
---

### Post by silentabe939 on 2008-05-22
So I want to use kde 4 but i have two issues at current.
1. How do i turn off that "touch to click" feature of laptop touchpads?
2. Is there an instruction manual because kde4 is a major changed and it has made me horribly confused.

Thanks

---

### Post by kuja on 2008-05-23
> **silentabe939 said:**
> So I want to use kde 4 but i have two issues at current.
1. How do i turn off that "touch to click" feature of laptop touchpads?
2. Is there an instruction manual because kde4 is a major changed and it has made me horribly confused.

Thanks

You can disable tapping in one of two perfectly good ways. One being to disable it via xorg.conf - 

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "MinSpeed" "0.45"
        Option          "MaxSpeed" "0.95"
        Option          "AccelFactor" "0.015"
        Option          "SHMConfig" "on"
        Option          "TapButton1" "0"
        Option          "TapButton2" "0"
        Option          "TapButton3" "0"

``` 
Notably the last three lines.

Another option is to download/compile touchfreeze, which is bascially qsynaptics replacement.

As per the changes ... exploring helps, and if all else fails pull up Konversation and drop by #kubuntu :)

---

