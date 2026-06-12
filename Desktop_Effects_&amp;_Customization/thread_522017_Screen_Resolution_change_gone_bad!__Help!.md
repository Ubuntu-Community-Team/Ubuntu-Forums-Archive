---
title: "Screen Resolution change gone bad!  Help?!?"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by Eion on 2007-08-10
After looking up on the forums here a way to update your screen res to a higher value I attempted to do so, and restarted X server, after restarting the borders are gone from all windows, and the terminal is completely white, I think it still works, I just can't see it.

I've attached pics of a window without borders, and the white terminal

---

### Post by jpeddicord on 2007-08-12
In that white terminal you had open, try running this:
```
metacity
```(Support Note: No --replace is needed, since it seems no window manager is running at all!)

If that gets you your window borders back, then close the window. Everything will flicker again, but the borders should reappear.

Jacob

---

