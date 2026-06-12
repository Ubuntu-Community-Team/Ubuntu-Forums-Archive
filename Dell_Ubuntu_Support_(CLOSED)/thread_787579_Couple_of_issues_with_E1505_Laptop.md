---
title: "Couple of issues with E1505 Laptop"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by doinfor on 2008-05-09
Not sure if this is the place to put this but I have been having a couple of annoying issues ever since upgrading to 8.04.

1. If I close the laptop with out shutting down, every 3rd or 4th time I cannot log in. I cannot see an arrow icon, but I do see the log in screen. I wind up having to press the power button and rebooting the system.

2. Increasingly I am having what I can best describe as a screen freezing up. The screen will not go blank, but rather it goes black and white. I am unable to do anything when this happens. Sometimes it comes back after only 10-20 seconds, sometimes it stays frozen. I can tell when this is going to happen by watching the hard drive tattle light, it stays lit.

This is happening on a Dell Inspiron E1505, that ran very well with 7.10 and had been doing so for a long time. Love Ubuntu, and will not get rid of it, but these things are annoying.

---

### Post by fatfranko on 2008-05-09
i had the same problem with my friend's dell d400.  i found this fix on a bug report from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256)

> 
The fix for this issue is to quirk your card to force enabling Pipe A. If you suspect you're having this bug, try setting this option in your xorg.conf:

  Section "Device"
    ...
    Option "ForceEnablePipeA" "true"
  EndSection


---

### Post by fatfranko on 2008-05-09
actually, in reading your post again, i'm not sure if its the same problem.  in my case, the screen would actually go black and i would have to manually shutdown.  if you have an intel-based graphics card, then you should try the fix i quoted and see if it helps.

---

### Post by doinfor on 2008-05-12
Update:

The issue has gotten worse- screen freeze almost every time I start up, and now the log in problem is everytime. How is this not a bug issue, when all that was done was to upgrade to 8.04?

---

