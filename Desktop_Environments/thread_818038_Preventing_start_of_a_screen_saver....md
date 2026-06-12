---
title: "Preventing start of a screen saver..."
date: 2008-06-04
forum: Desktop Environments
---

### Post by DeVelaine on 2008-06-04
Being that I have a TV tuner card and my gaming consoles hooked to my computer, I've been known to spend long periods of time with tvtime running full screen and not doing anything else. However, if I don't touch anything else for extended periods of time, the screen will fade as the screen saver kicks in.

Is there any way to tell KDE (or any desktop environment really) to not process the screen saver if a specific program is running? Or am I just hoping for something that hasn't been programmed yet?

---

### Post by wdaniels on 2008-06-04
You can use [xdg-screensaver]("http://portland.freedesktop.org/xdg-utils-1.0/xdg-screensaver.html") for this although you'll need to give it a window ID, not a process. Easy way to get a window ID is to use xwininfo and click on it. Would be simple enough to automate in a script I suppose, unless somebody else knows a simpler generic method?

---

### Post by Xiong Chiamiov on 2008-06-05
Some applications, particularly movie players, do so, so I suppose there should be some relatively easy method that they use.  I'm actually curious about this because KMPlayer doesn't, so I've been forced to set my screensaver time to 30 minutes (slightly over one anime ep).

---

