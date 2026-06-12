---
title: "Latitude D420/620/820 mouse question"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by bimmerd00d on 2007-08-01
So my D820 has the touchstick and the touchpad, with 4 total mouse buttons.  I generally use the touchstick only, how can i make the 2 lower buttons below the touchpad scroll up and down?  I had a Toshiba 6100 that had up/down scroll buttons and i miss that like crazy.  Here's my xorg.conf mouse section.  Also, is it possible to comment out the Wacom stuff from xorg.conf?  Will it make any difference?  I have no plans to ever use a wacom tablet or anything like that.

```

Section "InputDevice"
   Identifier   "Synaptics Touchpad"   # Don't change this from whatever value you have set already.
   Driver       "synaptics"
   Option       "SendCoreEvents"        "true"
   Option       "Device"                "/dev/psaux"
   Option       "Protocol"              "auto-dev"
   Option       "LeftEdge"              "130"
   Option       "RightEdge"             "840"
   Option       "TopEdge"               "130"
   Option       "BottomEdge"            "640"
   Option       "FingerLow"             "14"
   Option       "FingerHigh"            "15"
   Option       "MaxTapTime"            "180"
   Option       "MaxTapMove"            "110"
   Option       "ClickTime"             "0"
   Option       "MaxDoubleTapTime"      "100"
   Option       "EmulateMidButtonTime"  "75"
   Option       "VertScrollDelta"       "20"
   Option       "HorizScrollDelta"      "20"
   Option       "MinSpeed"              "0.60"
   Option       "MaxSpeed"              "1.10"
   Option       "AccelFactor"           "0.030"
   Option       "EdgeMotionMinSpeed"    "200"
   Option       "EdgeMotionMaxSpeed"    "200
   Option       "UpDownScrolling"       "1"
   Option       "CircularScrolling"     "1"
   Option       "CircScrollDelta"       "0.1"
   Option       "CircScrollTrigger"     "2"
   Option       "SHMConfig"             "true"
   Option       "Emulate3Buttons"       "on"
EndSection

```

---

### Post by mikeos on 2007-08-09
Feel free to comment out the Wacom stuff, unless you use Graphire or another model of Wacom tablets.

As to your question about scrolling, IMO those two buttons in the bottom are wired together with the two buttons on the top next to the  space-key.  

There are two options however which you may find may interesting:

1) Change the touchpad scrolling area to 0-100%/0-100% in your xorg.cong, which will disable pointing feature of the touchpad and it will become a dedicated "scrolling-pad". I did this, since the only thing I need for navigation is the glide-point. Search the web for more details about the modification or simply have a look at this piece of my xorg.conf:

```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "On"
    # Modify pointer speed (useless when dedicating all the surface for scrolling?)
    Option         "MinSpeed" "0.2"
    Option         "MaxSpeed" "1.2"
    Option         "AccelFactor" "0.05"
    # Maximize the scrolling area
  [B]  Option         "LeftEdge" "0"
    Option         "RightEdge" "1"
    Option         "TopEdge" "0"
    Option         "BottomEdge" "1"
    Option         "TapButton1" "0"
    Option         "TapButton2" "0"
    Option         "TapButton3" "0"[/B]
    # The above non-standard settings for the edges
[B]    Option         "RTCornerButton" "0"
    Option         "RBCornerButton" "0"
    Option         "LTCornerButton" "0"
    Option         "UpDownScrolling" "1"[/B]
    # Next line has currently no effect in Xorg
    Option         "LeftRightScrolling" "1"
EndSection

```

2) Emulate the middle mouse button with Win-Key or Caps Lock (mostly unused, yet handy positioned in the keyboard layout). Currently I have the Caps-Lock key being "morphed" into the middle mouse button, which allows me to scroll by glide point while holding it. See my other posts in this forum to find out more on this one. It's a kind of hack, but not so awful one.

I hope to have helped you at least partially.

---

