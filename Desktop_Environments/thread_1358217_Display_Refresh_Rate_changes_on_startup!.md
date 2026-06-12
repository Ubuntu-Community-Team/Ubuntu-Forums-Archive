---
title: "Display Refresh Rate changes on startup!"
date: 2009-12-18
forum: Desktop Environments
---

### Post by OVERPOWER8 on 2009-12-18
Hello.

Some time ago I have encountered a problem:
When I restart (or shutdown and turn on) the computer, refresh rate changes to 60 Hz.
_(1152*864 : 85) is saved to X Configuration File!_
* After the bootscreen (when the screen is black), resolution is fine (1152*864 : 85).
May be it's loaded from X Configuration File.
* BUT then the resolution changes to 60 Hz, and Desktop loads.
I Don't know what's happening, but may be some autorun program or service does something with refresh rate.

That's very annoying. I have to open nvidia-setings to change the refresh rate.
I don't know what I have done, but before that didn't happen.

I use:
Ubuntu 9.04
CRT monitor
Resolution 1152*864 : 85 Hz
System and Drivers are fine

Can someone explain, why may this be happening and how to fix that?

---

### Post by juliobahar on 2009-12-22
please post the output of the following code:
$ xrandr -q

and what type of video card are you using?

---

