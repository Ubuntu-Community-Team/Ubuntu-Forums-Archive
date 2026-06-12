---
title: "Application menus sometimes open on top of screen"
date: 2011-10-01
forum: Desktop Environments
---

### Post by zoisli on 2011-10-01
Hi there,

I have a very annoying problem here and no solution after hours of googling...
The problem is that some applications do not open their application menus correctly. See attached screenshots where I clicked on the "tools" menu of Clementine, and note that you can see some of the menu items at the top of the right screen.

A few more facts that I discovered so far:
- It only happens in a **few applications**: So far I had only problems with jEdit and Clementine
- It is **intermittent**! This is very surprising to me. Sometimes, all of a sudden, the menus display correctly! But this is usually not for all menu items, so e.g. it could be that the "tools" menu suddenly opens correctly, but the "music" menu is still buggy!
- On the left screen, nothing happens when I click a menu item. Not even something on the top of the screen. Nothing.
- When I boot up with only the left monitor (internal laptop monitor), the problem disappears

Environment:
Ubuntu 11.04 (Natty) with Gnome 2.32.1
Effects are disabled (when logging in:"Ubuntu classic (no effects)")
My xorg.conf contains the following (this was necessary to use the two monitors at the same time)
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Virtual         2944 1600
        EndSubSection
EndSection
```
Note that I cannot test with Unity, since it seems to have an issue with my screen setup and/or compiz...

Can anybody give me a hint what could be triggering this behavior?
Is there somebody having the same issues?

Thanks,
zoisli

---

