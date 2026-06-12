---
title: "xgamma settings overwritten at login"
date: 2012-03-12
forum: Desktop Environments
---

### Post by protossor on 2012-03-12
I tried to use xgamma to calibrate my screen color in newly installed ubuntu 11.10. In order to save the settings, I added the following commands at the startup managers.

xgamma -gamma 0.8

I can see the color change of my screen during the login process, however, every time right before my desktop shows up, the screen color will change back to gamma 1.0.
So, it seems the xgamma commands or similar commands are executed again after startup calls it, and changes the gamma settings back. Any idea to stop the gamma setting from changing back?

Thanks !

---

### Post by nll on 2012-07-12
I have the same problem. I looked around and found out that in /etc/X11/xorg.conf there should be a "Monitor" section where we could setup gamma. Look what's in this file.

Unfortunately for me all I see in my xorg.conf is the following:

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

No gamma setting anywhere. :confused:

---

### Post by nll on 2012-07-12
Hey, I found something that could work! Try the solution proposed in this thread: [http://ubuntuforums.org/showthread.php?t=1956897](http://ubuntuforums.org/showthread.php?t=1956897)

---

