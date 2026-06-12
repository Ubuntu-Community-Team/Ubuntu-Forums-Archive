---
title: "left and right window borders missing"
date: 2012-10-27
forum: Desktop Environments
---

### Post by ccrs8 on 2012-10-27
After upgrading Xubuntu from 12.04 to 12.10 (and therefor XFCE 4.8 to 4.10), the left and right borders of my windows are missing.  Besides looking funny, it also means that the only way I can resize a window's width is to use the multi-directional resize areas in the four corners of a window.

I am running the xfce style in "Appearance" and the default style in "Window Manager."  I believe these are what you get when you log in to the "XFCE session" as opposed to the "Xubuntu Session" at the display manager.

This only happens on my desktop - my laptop has the same xfce configuration and works fine.  My desktop uses the NVIDIA proprietary drivers while my laptop uses no proprietary drivers.

If I change the Window Manager style to almost anything else, the left and right borders appear (the only other one that does not work as far as I can tell is "Default 4.8."  So I'm sure I can find a Window Manager style I like that works, but I'd like to figure this out for curiosity sake.

Any ideas?

---

### Post by Toz on 2012-10-27
You might be experiencing this bug: [https://bugs.freedesktop.org/show_bug.cgi?id=54168]("https://bugs.freedesktop.org/show_bug.cgi?id=54168"). Appears to affect ATI/Nvidia proprietary drivers and window manager themes with 1 pixel-wide borders.

---

### Post by ccrs8 on 2012-10-27
Yeah, I agree - that seems to be the problem.  I'll follow that bug report.  Thanks!

---

