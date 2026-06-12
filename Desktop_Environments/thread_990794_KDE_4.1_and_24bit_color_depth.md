---
title: "KDE 4.1 and 24bit color depth"
date: 2008-11-23
forum: Desktop Environments
---

### Post by qyot27 on 2008-11-23
I noticed after installing KDE that the color depth was set to 16bit (as apparent from the ugly color gradiations on the default wallpaper and even moreso on the one I set myself).  Strangely, Gnome - or at least Eye of Gnome - didn't suffer from this, and neither did Gwenview ***when running under KDE***.  I did notice that Fluxbox also suffered from the bit depth problem as well.

So, after looking a bit, the solution was to add a line to xorg.conf that forced 24 as the bit depth.  So, I go ahead and do that.  Fluxbox's issue is resolved, Gnome is just like it always was, but KDE doesn't seem to like it.  As it loads, the screen blanks to white, then to black, and seems not to load at all.  I have to do a Ctrl-Alt-Backspace to get back to GDM.

Is there some KDE-specific file that needs to be adjusted here, or another setting in xorg.conf that I need to look at?  Maybe a log file that can illuminate where the issue itself lies?

This problem has been mentioned before, but seemingly only in passing, and I couldn't find any solution posted for it, so I'm asking here.

---

### Post by qyot27 on 2008-11-25
Ok, the problem got solved.  It stems from the fact that I hadn't turned off Compositing (which I should have, considering that my hardware doesn't support compositing).  If I had Compositing on and the DisplayDepth in xorg.conf was 16, it worked.  If I raised it to 24, it failed.  But going into ~/.kde/share/config/kwinrc and turning Compositing to Enabled=false fixed things for 24-bit color.

---

