---
title: "Dual display vertically aligned"
date: 2010-02-11
forum: Desktop Environments
---

### Post by log0 on 2010-02-11
Hi all,
I observed unexpected behavior when setting dual screen with the second monitor on top of the other:
========
|                |
|       2       |
|                |
========
========
|  G panel   |
| ----------- |
|       1       |
========

- The gnome panel covers up title bar of maximized windows.
- Menus from the Gnome panel don't expand properly.
Finally
- Windows released at the bottom of the second monitor unexpectedly stick (top side) to the top of the first screen.

Any help welcomed,
Thanks you
log0

---

### Post by log0 on 2010-02-11
Sorry for the ascii-art failure but I think you got my point )

---

### Post by drew010 on 2011-02-18
I can second that.  See attached screenshots.

Bottom screen is the built in laptop display (1366x768), top monitor is external (1680x1050).

Before-resize shows firefox unmaximized, title bar, close button are visible; after maximizing firefox, notice that the title bar, minimize, maximize, and close buttons are not visible as they are being covered by the panel.  It makes it a bit annoying to close or manipulate that window.

Running 10.10 x64, latest updates.

On another note, when I set the "secondary" monitor (doesn't seem to be a way to differentiate them) to be the one on top of the other, it insists on putting my desktop icons on the top monitor.  Even hitting set default on the bottom monitor and rebooting has no effect.  So it is deciding for me that my icons should go on the top monitor even though my primary panel remains on the laptop display.  Moving the secondary monitor to the left or right of the laptop display results in the icons showing on the laptop display.

Also, we are still suffering from the mouse voids with different resolutions as seen here [https://bugs.launchpad.net/ubuntu/+source/libxrandr/+bug/373367/](https://bugs.launchpad.net/ubuntu/+source/libxrandr/+bug/373367/)

Guess I'll have to do my linux development on Windoze since it makes life easier by supporting dual monitors :(

---

### Post by drew010 on 2011-02-18
Playing around some more I found a couple of things out:
1.  If I align the left edge of each monitor in the Monitors applet, maximizing the window results in the top bar being covered by the top panel on the bottom monitor
2.  If I offset the bottom laptop display a little bit to the right of the top monitor, maximizing the window works, but I have the undesired side effect of my primary laptop display being cut off on the left side and having a black void on the right, so that doesn't work either but it fixes the maximize issue.
3.  Also for some reason, if I try to drag a window from the bottom laptop display to the top external display, as soon as I drop it, it pushes the window back to the laptop display, so in effect it won't let me put anything on my top monitor by dragging.
4. If I set the top panel on the bottom (laptop) display to auto-hide, when it hides itself, it moves up to the bottom of the top (external) display, so it thinks it is hiding but it's really just moving up to the bottom of the other monitor getting in my way there.  I guess that's why the maximize gets broken, because it doesn't know really where the top and bottom monitors end and begin maybe.
I believe this functionality is just broken.

---

