---
title: "All GNOME  panels broken, every time"
date: 2010-06-03
forum: Desktop Environments
---

### Post by johann_p on 2010-06-03
I just installed Ubuntu 10.04 on a PC for one of my kids and everytime one logs in, the panels (both top and bottom) do not show any icons, and about one fourth of the rightmost part of the panel is completely missing.
This happens even when one completely removes the panel dir under .gconf and starts from scratch. 

Everytime the panel is somehow changed (e.g. by changing its size) it magically appears in its full glory. Killing the panel processes makes them also reappear correctly. 

Although there is the workaround of killing or changing the size every time after log in, this is rather annoying. 

Any advice how that could be solved?

---

### Post by wojox on 2010-06-03
Try these two commands

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by stubrn on 2010-06-04
you can also replace gnome-panel with another one like avant-window-navigator for example which i use and completely disable gnome-panel. the only problem is that it doesn't restarted automatically if killed or crash but i'm really not a gnome-panel fan so..

you can use gconf-editor or run this command in terminal:
```
gconftool-2 --type string --set \
/desktop/gnome/session/required_components/panel \
"avant-window-navigator"
```

---

### Post by johann_p on 2010-06-11
> **wojox said:**
> Try these two commands

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

This did not help. It reset the panel to the default and seems to do exactly the same as when I removed .gconf/apps/panel 
However, the default panel shows exactly the same problem - the right part is missing and no icons are shown :(

---

