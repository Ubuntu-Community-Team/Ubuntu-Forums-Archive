---
title: "Configuring the touch pad on Inspiron 1420n"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by n6k6t6 on 2008-02-13
Hi Everybody,

I just got an Inspiron 1420n with ubuntu 7.10.  
I tried to edit this section of xorg.conf :

Section "InputDevice"
        Identifier      "Synaptics Touchpad"

in order to  make 3 tweaks:
1) Get the cursor move faster, 
2) Disaple click on tap 
3) Disable vert edge scroll in favor of two-finger scroll macbook style.

I got the first two, and I can disable vert edge scroll, but only via
system->preferences->mouse->touchpad tab.  However I cannot get two finger scroll to work.   Plese someone tell me if it is possible to get two finger scroll to work on 1420n.   Here is the current state of my xorg.conf:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "TapButton1"            "0"      
        Option          "VertTwoFingerScroll"  "1"
        Option          "HorizTwoFingerScroll" "1"
        Option          "VertScrollDelta"      "20"
        Option          "HorizScrollDelta"     "50"  
        Option          "MinSpeed"             "1.10"
        Option          "MaxSpeed"             "1.30"
        Option          "AccelFactor"          "0.08"
EndSection

---

### Post by n6k6t6 on 2008-02-15
After some googling I have decided that dell inspiron 1420n touchpad does not support two-finger scroll.

---

