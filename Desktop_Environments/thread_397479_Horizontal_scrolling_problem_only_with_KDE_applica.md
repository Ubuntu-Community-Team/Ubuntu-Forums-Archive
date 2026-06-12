---
title: "Horizontal scrolling problem only with KDE applications"
date: 2007-03-30
forum: Desktop Environments
---

### Post by medomedo on 2007-03-30
Hello everybody,


I have a strange problem. I can scroll horizontally using my touchpad on GTK applications (Firefox, amule) but not with KDE applications (Konqueror and Kmail).

I tried to make some changes with ksynaptics but no success. The relavant Xorg.conf section is:
```
Section "InputDevice"
        Identifier      "Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option        "LeftEdge"      "1700"
        Option        "RightEdge"     "5300"
        Option        "TopEdge"       "1700"
        Option        "BottomEdge"    "4200"
        Option        "FingerLow"     "25"
        Option        "FingerHigh"    "30"
        Option        "MaxTapTime"    "180"
        Option        "MaxTapMove"    "220"
        Option        "VertScrollDelta" "100"
        Option        "MinSpeed"      "0.09"
        Option        "MaxSpeed"      "0.18"
        Option        "AccelFactor" "0.0015"
        Option          "SHMConfig" "on"
        Option          "Emulate3Buttons"       "true"
EndSection

```

As you know using touchpad with horizontal scrolling is very helpful.
Any idea/hint is appreciated

---

### Post by medomedo on 2007-04-20
Hi again,

It turns out that the cause of the problem is the Domino style. When I switched to another style like plastik, KDE applications behaved as expected (horizontal scrolling is working).

---

