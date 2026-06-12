---
title: "alt+scroll for window opacity in xfce4"
date: 2014-06-07
forum: Desktop Environments
---

### Post by leptogenesis2 on 2014-06-07
In ubuntu, if you hold alt and scroll with the mouse, the window opacity changes.  I've seen posts saying that the behavior should be the same in xubuntu 14.04, but for me, alt+scroll zooms in and out.  I can't find any way to change the opacity of a single window or the behavior of the mouse shortcuts.  The window manager tweaks lets me change the opacity for all windows, so I know the desktop environment supports this.  I use this as a quick-and-dirty way to compare scientific plots; in general, I only want a single window to be transparent at a time, and it's pretty essential for my workflow.

---

### Post by Toz on 2014-06-07
Hello and welcome to the forums.

In Xfce (Xubuntu), the mouse needs to be positioned on the window's title bar for the opacity to change.

---

### Post by leptogenesis2 on 2014-06-07
Tried that; for me, even when the mouse is positioned over the title bar, alt+scroll still just zooms.

---

### Post by Toz on 2014-06-07
Ok, I know what's happening. If you go to Settings Manager >> Window Manager Tweaks >> Accessibility tab, there is a setting for "Key used to grab and move windows". If its set to ALT, then the zoom feature will override the transparency feature. You need to change ALT to another key for grabbing the window, then the transparency/opacity will work. The zoom feature will also then work with the new key that you specified (along with regular window-grabbing functions).

---

### Post by leptogenesis2 on 2014-06-07
That did it!

---

