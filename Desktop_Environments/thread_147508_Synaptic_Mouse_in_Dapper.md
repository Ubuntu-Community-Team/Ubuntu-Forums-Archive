---
title: "Synaptic Mouse in Dapper"
date: 2006-03-20
forum: Desktop Environments
---

### Post by mdofl1 on 2006-03-20
Hello, I have recently upgrade to Dapper and my synaptic mouse on my laptop is no longer working well.  It works but the mouse motions are slower and it takes more strokes to move the mouse.  I have looked and I believe that the problem arises from the fact that a generic driver was installed instead of the one for the mouse pad.  Is there anyone who can tell me how to fix this?


TIA,
mdofl

---

### Post by Stealth on 2006-03-20
Yea, I noticed this too, but I copied my xorg.conf file straight from Breezy. I have this extra section in there for it:

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option "AlwaysCore"
    Option "Device" "/dev/input/event2"
    Option "Protocol" "event"
    Option "LeftEdge" "120"
    Option "RightEdge" "830"
    Option "TopEdge" "120"
    Option "BottomEdge" "650"
    Option "FingerLow" "14"
    Option "FingerHigh" "15"
    Option "MaxTapTime" "180"
    Option "MaxTapMove" "110"
    Option "ClickTime" "0"
    Option "EmulateMidButtonTime" "75"
    Option "VertScrollDelta" "10"
    Option "HorizScrollDelta" "0"
    Option "MinSpeed" "0.45"
    Option "MaxSpeed" "0.75"
    Option "AccelFactor" "0.020"
    Option "EdgeMotionMinSpeed" "200"
    Option "EdgeMotionMaxSpeed" "200"
    Option "UpDownScrolling" "1"
    Option "CircularScrolling" "0"
    Option "CircScrollDelta" "0.1"
    Option "CircScrollTrigger" "2"
    Option "SHMConfig" "true"
EndSection

This is for my Inspiron 9300, and I get good speed, and the lil scrollers and tapping working...

---

### Post by mdofl1 on 2006-03-20
Thanks for the help.  I copied your xorg file into mine and it worked perfectly.  


-C

---

