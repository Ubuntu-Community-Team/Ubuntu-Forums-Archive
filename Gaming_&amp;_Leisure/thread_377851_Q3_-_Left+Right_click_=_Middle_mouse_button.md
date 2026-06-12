---
title: "Q3 - Left+Right click = Middle mouse button?"
date: 2007-03-06
forum: Gaming &amp; Leisure
---

### Post by alextj on 2007-03-06
My friend is having a problem with mouse.
He uses left mouse button to fire and right mouse button to jump (in Quake 3).
Now there comes a problem when he wants to jump and fire at the same time:
pressing both buttons at once will give same result as pressing middle mouse button, and no jumping neither firing!

I noticed the same, though, I use different configuration and it doesn't bother me, but my friend can't play. Changing controls is not an option, he have been playing with this setup for years on Windows and there is no way he will change his keys. Something needs to be done to this mouse button behavior.

On Linux it's like Left + Right = Middle. Is there a way to change this?

Thanks!

---

### Post by colo on 2007-03-06
Yes, there is - you need to tell your X-Server (the application responsible for graphical output on your screen) to not behave like this. This is acchieved by adding
```
Option "Emulate3Buttons" "false"
```
to the mouse-specific section of your /etc/X11/xorg.conf

You need to have super-user privileges to be able to edit the file. Restart your graphical desktop after you added said line, and you should be done.

On my system (Gentoo, not Ubuntu, though) my mouse-configuration looks like this:
```
Section "InputDevice"
        Identifier              "MOUSE0"
        Driver                  "mouse"
        Option                  "Protocol"      "ExplorerPS/2"
        Option                  "Device"                "/dev/input/mice"
        Option                  "Emulate3Buttons"       "false"
EndSection
```

---

### Post by alextj on 2007-03-06
Thank you Colo! That was rather simple answer.
Cheers
:)

---

