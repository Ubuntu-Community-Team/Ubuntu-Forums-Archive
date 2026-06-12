---
title: "D630+ Port Replicator = Touchpad stops working like a touchpad"
date: 2008-01-13
forum: Dell  Ubuntu Support
---

### Post by Nicolae on 2008-01-13
I have my touchpad set up so the entire thing is a huge scrolling pad, since I can't stand using it as a pointing device and I miss having a mousewheel. However, when I dock the laptop the touchpad starts behaving like a pointing device. The touchpad normally is /dev/input/event4, and the trackpoint is /dev/input/event3. When I dock, the touchpad starts writing to /dev/input/event3 (I.E, cat /dev/input/event3 gets something for both using the trackpoint and touchpad after I dock, and only the trackpoint before). To get the touchpad working properly again, I have to rmmod and modprobe psmouse, which assigns the trackpoint and touchpad new  events, and then restart X to get it to use the new events. It does not happen if I hibernate when off the dock, then resume after I dock, or vice-versa but does happen when I undock when running. It's kind of annoying, and I was wondering if anyone had run into this issue (in theory, it will also render the scrolling area on a normal touchpad nonfunctional as well) or knew of a way to fix it.

---

### Post by sovietfunk on 2008-01-18
I have the same problem, with a Precision M65 (identical to Latitude 830, i believe). My trackpad is set up normal, with scrolling in a small area to the right. When I undock, the trackpad loses the scrolling area, but works fine just tracking. Going back to dock is something I haven't dared try out for a while, since with Dapper and Feisty the system would freeze. Haven't tried yet with Gutsy. Generally I'd reboot and dock when the laptop reached "flatline". 

Annoying but I haven't been able to find out anything myself, yours is the first post i have found which looks identical to my problem.. Will try your methods and see if i can help us find better ways. 

Here's my trackpad section from xorg.conf:
```
Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver  "synaptics"
 Option  "InputFashion"  "Mouse"
 Option  "SendCoreEvents" "true"
 Option  "Device"  "/dev/psaux"
 Option  "Protocol"  "auto-dev"
 Option  "HorizScrollDelta" "0"
 Option  "SHMConfig"  "on"
 Option  "RTCornerButton" "0"
 Option  "RBCornerButton" "0"
 Option  "TapButton1"  "0"
 Option  "TapButton2"  "0"
 Option  "TapButton3"  "0"
 Option  "Buttons"  "8"
 Option  "ZAxisMapping"  "4 5 6 7"
 Option  "TopEdge"  "100"
 Option  "BottomEdge"  "670"
 Option  "LeftEdge"  "100"
 Option  "RightEdge"  "950"
 Option  "MaxSpeed"  "2.0"
 Option  "MinSpeed"  "0.5"
 Option  "AccelFactor"  "0.05"
EndSection

```

---

### Post by sovietfunk on 2008-01-18
If the problem is with the touchpad changing input device, is this something that can be tweaked in /etc/udev/rules.d/65-persistent-input.rules?

---

### Post by Nicolae on 2008-01-18
It might, but I have to wonder if the problem is the sudden appearance of the PS/2 ports on the port replicator. My trackpoint detects as a PS/2 device, and I wonder if it's bumping the touchpad so the PS/2 port will work. I've an old PS/2 mouse I'll test this with later.

---

