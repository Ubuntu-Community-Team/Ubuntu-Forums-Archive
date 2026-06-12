---
title: "[SOLVED] locked out of desktop! please help."
date: 2007-06-19
forum: Desktop Environments
---

### Post by toobuntu on 2007-06-19
For the past week/week-and-a-half, whenever I have a locked screen (from gnome-typing-monitor, gnome-screensaver, or just by locking the screen) keyboard input is not being grabbed.  Mouse movements happen like normal, but no keyboard input is grabbed.

I "Switch User" and restart the machine to get me back in, but that is obviously not a long-term solution.

Separately, gksudo has been broken for the past few weeks, and I cannot launch any administrative app with a gui unless it will invoke with sudo <app-name> from a terminal window.

Please help!

Ubuntu 2.6.20-16-lowlatency
Beryl
Dell standard USB keyboard and optical USB mouse, US English layout

---

### Post by Hatchetfish on 2007-06-19
I've been having the same issue with the screensaver & beryl (only happens when running beryl) for several weeks.  the 'workaround' that isn't tends to get old pretty quick, so I've only been using beryl intermittently.

---

### Post by toobuntu on 2007-06-22
found a solution to fix situation when beryl is running and screen is locked...unable to click the password box or type into it (no probs under metacity, though):

Beryl Settings Manager->General Options->Advanced->Unredirect Fullscreen Windows

---

