---
title: "Need help configuring a 9 button mouse (buttons 6 and 7 don't respond)"
date: 2009-10-17
forum: Desktop Environments
---

### Post by OrangeVixen on 2009-10-17
As the title says.

I'm still working on trying to get buttons 6 and 7 to respond.

This is a MicroInv mouse, their web site has no drivers for Linux.

Here is my mouse section in xorg.conf:

```

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
# Option "Protocol" "USB"
Option "Device" "/dev/psaux"
# Option "Device" "/dev/input/mouse1"
Option "Buttons" "9"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

```

I've already tried the USB Protocol and a couple of others, but I'm not sure what else to do.

Using xev, the buttons are as follows:

Button1 - standard left button
Button2 - wheel if you press straight down
Button3 - standard right button
Button4 - wheel rolling
Button5 - wheel rolling
Button6 - not responding
Button7 - not responding
Button8 - left side button or wheel press left
Button9 - right side button or wheel press right

It's 's the wheel press left and right that shound be triggering buttons 6 and 7.

I already tried gpointing-device-settings but it's for 2 button mice.

I tried to open /dev/input/mouse1 and I did get data when I pressed the wheel left and right, so I think it maybe that X is not reporting it correctly?

---

