---
title: "Logitech MX518 USB, mouse speed acting weird in Gnome"
date: 2005-12-04
forum: Desktop Environments
---

### Post by keitsi on 2005-12-04
Hello.

First of all before someone gets to say "RTFM", I've done this Logitech mouse guide:
[http://www.ubuntuforums.org/showthread.php?t=65471&highlight=mx518](http://www.ubuntuforums.org/showthread.php?t=65471&highlight=mx518)

It made the side buttons work with Opera, but didn't solve this problem.

When I set the Gnome mouse sensitivity from "low" to "high", it **only** affects the speed *sometimes* when cursor is over some GUI element like TextBox or such. I mean, suddently the mouse speed might go up to highest and when mouse cursor enters some other area in desktop, the speed drops back to very slow. Not easy to describe but I hope you get the idea. Weird? :P  ctually, I encountered similar problems in Windows as well when I used the Logitech driver implementation, so this might be somehow related to Logitech. Settings the MS implementation on helped. Currently I have to keep the mouse speed at the lowest possible setting for the mouse to be usable (that way the speed is always same, independant of the GUI object mouse cursor is moving over).

With the lowest setting, my mouse speed just isn't as much as it was in Windows with the Logitech SetPoint driver installed. I don't want to use mouse acceleration either, IMO that sucks especially in games. Mouse movement space depending on the speed of the movement, that just doesn't work for me, I always "overmove" the cursor with mouse acceleration enabled.

MX518 has a built-in DPI changer (the two small buttons next to scroll wheel), with that I can set between 400DPI, 800DPI and 1600DPI. Of course I'm using the 1600DPI mode but that isn't enough. If I move my mouse from left side of the desktop to the right side, my huge mouse pad is barely enough.

Anyway, here's some technical details if someone wants to look at them:
```

keitsi@keitsi:~$ cat /proc/bus/input/devices
I: Bus=0003 Vendor=046d Product=c215 Version=3500
N: Name="Logitech Logitech Extreme 3D Pro"
P: Phys=usb-0000:00:1d.3-2/input0
H: Handlers=event0 js0
B: EV=b
B: KEY=fff 0 0 0 0 0 0 0 0 0
B: ABS=30063

I: Bus=0003 Vendor=046d Product=c309 Version=1500
N: Name="Logitech Logitech USB Keyboard"
P: Phys=usb-0000:00:1d.0-1/input0
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c309 Version=1500
N: Name="Logitech Logitech USB Keyboard"
P: Phys=usb-0000:00:1d.0-1/input1
H: Handlers=kbd mouse0 event2 ts0
B: EV=f
B: KEY=ffffffff ffffffff 0 0 1878 d801d108 1e0000 0 0 0
B: REL=103
B: ABS=3ff00 0

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event4
B: EV=40001
B: SND=6

```

Xorg mouse settings:
```

#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
#       Option          "Protocol"              "ImPS/2"
#       Option          "Emulate3Buttons"       "true"
#       Option          "ZAxisMapping"          "4 5"
#EndSection
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
        Option        "Protocol"        "evdev"
        Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
        Option        "Dev Phys"        "usb-0000:00:1d.0-2/input0"
        Option        "Device"          "/dev/input/event3"
        Option        "Buttons"         "10"
        Option        "ZAxisMapping"    "4 5"
EndSection

```

---

### Post by keitsi on 2005-12-04
Hmm... maybe I was thinking too quick.

I just realized that "Acceleration" in Gnome settings doesn't change the same acceleration as in Windows, instead it changes the "normal" mouse speed. I was able to set the speed to fast enough, and the movement rate is not dependant on movement speed.

Maybe the developers could add some descriptions to the mouse settings page, since "acceleration" can be a bit ambiguous? :P

Sorry for this unnecessary topic.

---

