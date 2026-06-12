---
title: "USB Joypad Problems in Edgy"
date: 2006-12-17
forum: Gaming &amp; Leisure
---

### Post by russo.mic on 2006-12-17
So, I've gotten 6.10 working great on my laptop, except for my Logitech USB Joypad.  It seems that I can get the buttons to work fine, but the axis won't function at all.  What is strange is that my Joystick Calibration utility seems to find them find, and calibrate them okay, but no application will respond to them.  I've tried gsnes9x, and amarok with the joystick script, and nothing works.  I've tried modprobe analog, but nothing.

Any ideas?  

Thanks in advance for any help anybody can give me!

---

### Post by herot on 2006-12-22
i read it in other topics ... and its weird... but unplug your USB gamepad and plug it back in... DONT calibrate it... it should work fine with mame or whatever now...

its a bug i hope they fix it soon

---

### Post by Danielito on 2006-12-29
I had the same problem with my logitech USB joystick. I could calibrate the joystick with jscalibrator and it seemed to be working properly, but with xMame I could use the buttons but I couldn't move the axis. 
I managed to get it working just installing the joystick package and then calibrating the joystick with jscal utility. Amazing.:confused:

---

### Post by fiath on 2007-01-23
> **herot said:**
> i read it in other topics ... and its weird... but unplug your USB gamepad and plug it back in... DONT calibrate it... it should work fine with mame or whatever now...

Aha! That worked for me too! Thanks! :D

> its a bug i hope they fix it soon

Heh, well they won't fix it if it is not reported. :)
I couldn't find anything like this in the bug tracker, so I did one:

[https://bugs.launchpad.net/ubuntu/+source/libjsw/+bug/81093](https://bugs.launchpad.net/ubuntu/+source/libjsw/+bug/81093)

If you know anything more about why this happens, please add your information!

---

