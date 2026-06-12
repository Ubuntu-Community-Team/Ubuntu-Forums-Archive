---
title: "After configuring Compiz, the desktop environment disappeared!"
date: 2011-10-01
forum: Desktop Environments
---

### Post by jalms on 2011-10-01
Dear fellows,

Today I was trying to enable the desktop 3D cube and I followed the instructions to do so in the Compiz Config.

After enabling them, I was prompted to disable the Desktop Wall and so I did.

Starting from that, only the Firefox browsing kept working, nothing else. Neither the app menu or anything else, all was completely locked.
I rebooted and logged in normally, at the "Ubuntu" option at the GUI login screen (as I always do). OS loads normally and, for instance, mail notifiers work at once. However, there's no top bar, neither unity bar on the left, no shortcut works (unless Ctrl+Alt+Del), only the desktop's wallpaper and its icons appear.

Rebooted and logged in safe mode, so I could disable the options that went wrong. So I did, and enabled Unity and Desktop Wall again, just as it was before.
Logged out and then logged in as "Ubuntu" again and still the same problem....

The only way I managed of "getting things normal" so far was logging as User Defined Session, but I confess my noobness and don't know what it is. How can I restore my "Ubuntu" normal session as it was before I messed up?

Thank you a lot in advance for helping me :)

---

### Post by jkpitzer74 on 2011-10-01
I have a similar issue. I ahve not been able to use the desktop since my upgrades installed.

---

### Post by jalms on 2011-10-01
Tried to login as "User Defined Session" or as "Ubuntu (Safe Mode)"?

---

### Post by Krytarik on 2011-10-01
Please see this troubleshooting guide:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

It includes this guide to enable the Cube:
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

And, as also referred to in the first guide, there are two profiles in CompizConfig Settings Manager, in "Preferences" (lower left):
- classic Gnome: "Default"
- Unity: "Unity"

Greetings.

---

### Post by jalms on 2011-10-01
I didn't care about the cube anymore, I just wanted my default Unity settings back!
So I followed your instructions on "Enable Ubuntu Unity Plugin", restarted GMD and everything was as it should be, except for the window title bars.
Just had to follow your tutorial under "Window Title Bars Missing".
And it's solved now, I can't tell you how much your help is appreciated. Thank you very much!!

---

