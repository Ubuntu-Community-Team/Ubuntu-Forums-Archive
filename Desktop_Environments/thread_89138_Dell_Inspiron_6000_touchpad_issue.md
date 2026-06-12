---
title: "Dell Inspiron 6000 touchpad issue"
date: 2005-11-11
forum: Desktop Environments
---

### Post by funbags on 2005-11-11
Hello,

I have a dell inspiron 6000, and the touchpad is so sensative that even the slightest touch activates a click. Below is my current config. Its so senative is almost unuseable..  If anything i would rather disable the touchpad clicks if there isnt another solution.  Thanks for the help in advance.



I have tried various configurations... This is my current one which i used after searching the forums


> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "0"
        Option          "HorizScrollDelta"      "0"
        Option          "MinSpeed"              "0.3"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.015"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        # local additions below
        Option          "SHMConfig"             "on"
        Option          "TapButton1"            "3"
        Option          "TapButton3"            "1"


EndSection

---

### Post by funbags on 2005-11-14
Any one ?

---

### Post by andrewski on 2006-04-09
1. The specific settings for your touchpad in your xorg.conf (i.e. the ones you pasted above) could contribute to the sensitivity; can you reproduce the sensitivity if you take those out?
2. Also, what about turning down the Sensitivity in the Mouse preferences?  That should help if you haven't tried it already.
3. If it suits you, you can [turn off tap-to-click](http://ubuntuforums.org/showpost.php?p=889122&postcount=2).  Search the forums for more information.

BTW, this has been reported on Launchpad: [https://launchpad.net/distros/ubuntu...ics/+bug/33788]("https://launchpad.net/distros/ubuntu/+source/xorg-driver-synaptics/+bug/33788").

For what it's worth, the synaptics driver has gotten a lot of attention for Dapper. For example, the side scrolling works by default. If you're up for upgrading to Dapper, we would love your feedback for how it works thereon.

---

### Post by thediviner on 2006-04-09
Sorry if this has already been taken care of. It might be possible to make the mouse tapping less sensitive by increasing the FingerLow and FingerHigh values to something like 25 and 30 respectively.

Once finger pressure exceeds the finger high value the touch pad registers it as a button-down, so increasing the value should increase the amount of finger pressure required for a click.

I hope this helps.

---

