---
title: "Using Dust Dark theme, can't see the menus?"
date: 2011-07-18
forum: Desktop Environments
---

### Post by garycheng12 on 2011-07-18
I've selected the Dusk Dark theme, but the menu names are of the same color (I have to look extremely closely at the monitor to see the names of the menus. I assumed the font color of the menu names would change to a color (such as white) that would contrast the near black color of the Dust Dark theme. How can I change this? Thanks.

By the way, I'm really uncomfortable with the Ubuntu layout. How can I switch to multiple windows without using Alt-Tab? Like access the Windows taskbar?

---

### Post by aliasyak on 2011-08-03
just ran into the same, solved it by adding "*text[NORMAL] = @selected_fg_color*" to section "*style "panel"*" in the Dust gtkrc file (/usr/share/themes/Dust/gtk-2.0/gtkrc) as described in [https://bugs.launchpad.net/unity/+bug/730968](https://bugs.launchpad.net/unity/+bug/730968).

You could use gnome classic (choosable at login screen) if you want something similar to the windows taskbar.

---

