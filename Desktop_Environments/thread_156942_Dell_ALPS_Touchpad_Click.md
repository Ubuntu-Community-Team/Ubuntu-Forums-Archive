---
title: "Dell ALPS Touchpad Click"
date: 2006-04-08
forum: Desktop Environments
---

### Post by dbunder on 2006-04-08
Yes, I'm the one person who actually likes it when you can click on your mousepad and get a click event.  I followed a synaptics/alps tutorial on here and that functionality disappeared.  I'd like it back, but I cannot for the life of me find out how to to do it.  Here's my ALPS config in xorg.conf:

Section "InputDevice"
  Identifier    "ALPS"
  Driver        "synaptics"

        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/input/event2"
        Option          "Protocol"              "event"
        Option          "SHMConfig"     "true"
        Option          "AlwaysCore"

        Option  "LeftEdge"              "120"
        Option  "RightEdge"             "830"
        Option  "TopEdge"               "120"
        Option  "BottomEdge"            "650"
        Option  "FingerLow"             "14"
        Option  "FingerHigh"            "15"
        Option  "MaxTapTime"            "0"

        Option  "EmulateMidButtonTime"  "75"
        Option  "VertScrollDelta"       "20"
        Option  "HorizScrollDelta"      "20"
        Option  "MinSpeed"              "0.6"
        Option  "MaxSpeed"              "1.5"
       Option  "AccelFactor"           "0.03"
        Option  "EdgeMotionMinZ"        "30"
        Option  "EdgeMotionMaxZ"        "160"
        Option  "EdgeMotionMinSpeed"    "15"
        Option  "EdgeMotionMaxSpeed"    "15"
        Option  "EdgeMotionUseAlways"   "0"
        Option  "UpDownScrolling"       "1"
        Option  "LeftRightScrolling"    "0"
        Option  "CircularScrolling"     "0"
        Option  "CircScrollDelta"       "0.1"
        Option  "CircScrollTrigger"     "0"
        Option  "TapButton1"            "1"
        Option  "TapButton2"            "2"
        Option  "TapButton3"            "3"
        Option  "LockedDrags"           "on"
EndSection

The TapButton directives don't do a thing, none of the other options in the manpage or elsewhere turn it back on.  Any ideas?  Thanks so much for any help.

---

