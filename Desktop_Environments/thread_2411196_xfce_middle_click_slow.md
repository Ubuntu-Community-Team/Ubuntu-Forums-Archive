---
title: "xfce middle click slow"
date: 2019-01-26
forum: Desktop Environments
---

### Post by dave72 on 2019-01-26
I have an odd problem on Xubuntu 18.04. I think it started when I upgraded recently, I thought the middle click on my scroll mouse was not working. My main uses are cut and paste, plus open new tab in a browser so it has become quite frustrating. After reading this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581088)
it seems it is just very slow to recognize. If I highlight some text in a terminal and hold down the middle button, it takes about 2 seconds before it pastes. One person on the above thread fixed this by changing the timeout option under xinput, but I don't have this:

```
Device 'Logitech USB Receiver':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Natural Scrolling Enabled (279):    0
    libinput Natural Scrolling Enabled Default (280):    0
    libinput Scroll Methods Available (281):    0, 0, 1
    libinput Scroll Method Enabled (282):    0, 0, 0
    libinput Scroll Method Enabled Default (283):    0, 0, 0
    libinput Button Scrolling Button (284):    2
    libinput Button Scrolling Button Default (285):    2
    libinput Middle Emulation Enabled (286):    1
    libinput Middle Emulation Enabled Default (287):    0
    libinput Accel Speed (288):    0.000000
    libinput Accel Speed Default (289):    0.000000
    libinput Accel Profiles Available (290):    1, 1
    libinput Accel Profile Enabled (291):    1, 0
    libinput Accel Profile Enabled Default (292):    1, 0
    libinput Left Handed Enabled (293):    0
    libinput Left Handed Enabled Default (294):    0
    libinput Send Events Modes Available (264):    1, 0
    libinput Send Events Mode Enabled (265):    0, 0
    libinput Send Events Mode Enabled Default (266):    0, 0
    Device Node (267):    "/dev/input/event6"
    Device Product ID (268):    1133, 50484
    libinput Drag Lock Buttons (295):    <no items>
    libinput Horizontal Scroll Enabled (296):    1
```

Pasting that seemed to take longer, closer to 5s.

Any idea how I can increase the speed of recognising the middle click?

---

