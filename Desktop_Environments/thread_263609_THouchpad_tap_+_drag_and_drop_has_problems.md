---
title: "THouchpad tap + drag and drop has problems"
date: 2006-09-23
forum: Desktop Environments
---

### Post by alanfranz on 2006-09-23
Hello, I'm experiencing what I think are hardware-unrelated problems with Ubuntu/Gnome.

I've got an ALPS touchpad using Synaptics driver, I've already configured it and it *seems* to work, but it doesn't always.

The mayor problem is the so-called 'one click and half': it's a double click, but the finger is not released from the touchpad after the second click.

This action should allow to drag and drop windows, to scroll lateral bars, and to move icons on the desktop.

I can always move icons on the desktop, no problems.
I *sometimes* can scroll lateral bars on some programs, sometimes I can't. Right now, I can scroll Firefox but not Gnome Terminal.
I *sometimes* can resize windows this way, but sometimes simply doesn't work.
I can never move windows around this way.

Any idea?I'm posting the appropriate section of my xorg.conf even though I suspect this is more gnome-related than synaptics-related.

```

Section "InputDevice"

        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option "Emulate3Buttons" "on"
        Option      "AlwaysCore"
        Option      "Device" "/dev/input/mouse0"
        Option      "Protocol" "auto-dev"
        Option      "LeftEdge" "130"
        Option      "RightEdge" "840"
        Option      "TopEdge" "130"
        Option      "BottomEdge" "640"
        Option      "FingerLow" "2"
        Option      "FingerHigh" "4"
        Option      "MaxTapTime" "180"
        Option      "ClickTime" "100"
        Option      "MaxTapMove" "20"
        Option      "EmulateMidButtonTime" "75"
        Option      "VertScrollDelta" "20"
        Option      "HorizScrollDelta" "20"
        Option      "MinSpeed" "1.00"
        Option      "MaxSpeed" "1.30"
        Option      "AccelFactor" "0.020"
        Option      "EdgeMotionMinSpeed" "200"
        Option      "EdgeMotionMaxSpeed" "200"
        Option      "UpDownScrolling" "1"
        Option      "CircularScrolling" "1"
        Option      "CircScrollDelta" "0.1"
        Option      "CircScrollTrigger" "2"
        Option      "PalmDetect" "False"
        Option      "SHMConfig" "on"
EndSection

```

---

