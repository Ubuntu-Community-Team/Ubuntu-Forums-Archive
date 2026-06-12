---
title: "Problems with resizing (any) windows in Awesome Window Manager"
date: 2013-02-20
forum: Desktop Environments
---

### Post by alas-poor-yorick on 2013-02-20
While trying to resolve my own problem, I came across a lot of forum posts with no replies with issues like "cannot resize windows" or "resizing window shortcuts do not work" or "cannot resize windows in some layouts", etc. This behavior has to do with a misunderstanding of how Awesome handles windows, but for the new user experiencing unexpected behavior, the symptoms do not match well with the terminology used in the documentation. Here is my experience and what I learned as a solution to this problem.

When I used the Mod4+h/l keyboard shortcuts or Mod4+right click to change the size of the windows, it would work at first, but it would sometimes seem to inexplicably stop working. On certain layouts, it would not work at all, and even after switching back to layouts where it had previously worked, it would stop working.

I eventually found this in the man page for awesome:

> In tiled layout windows are managed in a master and stacking area. The master area contains the windows which currently need most attention, whereas the stacking area contains all other windows. In floating layout windows can be resized and moved freely. Dialog windows are always managed floating, regardless of the layout applied. The spiral and dwindle layout are special cases of the tiled layout where the stacking area is arranged in a spiral for the former or as a rectangular fractal for the later.

The thumbnail in the top right corner for the tiled layouts is supposed to show the division between the master area and the stacking area. What the user experiences as "resizing" is controlled by two properties within each layout: The "master width factor" and the number of master windows. The Master width factor determines where the line between the two areas is. Mod4+h increases the master width factor, meaning the master area becomes smaller, and Mod4+l does the opposite.

There were two reasons I was having problems. One is that changing the master width factor is not supported in some layouts, so in those layouts, the shortcuts will not work. The other problem was that, in attempting to find a keyboard shortcut that would fix resizing, I would try Mod4+shift+h/l. Instead of reversing the effect of a Mod4+h/l, this shortcut increases or decreases the number of master windows by 1. So if two windows are open, one in the stacking area and one in the master area, and I increase the number of master windows by 1, the window in the stacking area will move to the master area. Now that all windows are in the master area, changing the master width factor will not change how the windows are displayed. To correct this, change the number of master windows back using the other Mod4+shift+h/l shortcut. Restarting Awesome also resets the number of master windows to the default.

Hopefully this is helpful to someone. Happy resizing!

---

