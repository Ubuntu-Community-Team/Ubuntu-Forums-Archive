---
title: "Compiz: Focus previously active window upon window close"
date: 2009-10-25
forum: Desktop Environments
---

### Post by quux on 2009-10-25
I'm running compiz 0.8.4 on an Ubuntu Karmic Gnome desktop in click-to-focus-mode and noticed a change in focus behavior when compared to previous compiz versions.

Suppose you open two windows on a virtual desktop. Each of those windows gets the focus once it appears as usual.

If you close the second (and currently active) window, I'd expect the first window to receive the focus. At least that's the focus model I remember from previous compiz versions (and Metacity as well).

However, in 0.8.4 the window which is currently under the mouse pointer receives the focus instead once the active window is closed. If there's currently no window under the mouse cursor, then no window is being focused.

Is this just a configuration problem on my side or was there indeed a change in the way compiz handles window focus in this case? In the latter case, is there any way to get the old focus behavior back?

---

