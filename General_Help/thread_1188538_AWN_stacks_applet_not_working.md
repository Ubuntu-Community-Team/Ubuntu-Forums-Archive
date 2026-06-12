---
title: "AWN stacks applet not working"
date: 2009-06-15
forum: General Help
---

### Post by yoshi445511 on 2009-06-15
EDIT: First post :D
So, i've been trying to install mac4lin all day and now i'm trying to get the stacks applet on AWN, but when i activate it all that shows is a vertical line. I've scoured the forums for hours but can't get it to run...

heres what it says when i run awn:
```
fuzzy@theawesomemobile:~/.config/awn/applets/stacks$ awn
Screen is composited.
LOADED : /usr/share/applications/awn-manager.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/places.desktop
APPLET : /usr/share/avant-window-navigator/applets/stacks.desktop

(awn:12290): Gdk-CRITICAL **: gdk_x11_atom_to_xatom_for_display: assertion `atom != GDK_NONE' failed

(awn:12290): Gdk-CRITICAL **: gdk_x11_atom_to_xatom_for_display: assertion `atom != GDK_NONE' failed
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/stacks/stacks_applet.py", line 22, in <module>
    import gtk
ImportError: No module named gtk

** (awn-applet-activation:12292): WARNING **: Places: XDG_DESKTOP_DIR is not set... defaulting to "~/Desktop"



```any help would be greatly appreciated.

---

### Post by yoshi445511 on 2009-06-15
anyone?

---

### Post by rocketman768 on 2009-06-15
AWN sucks. You will find out.

---

### Post by jeneverboy on 2009-09-07
> AWN sucks. You will find out. 

What do you suggest as alternative?

---

### Post by jeneverboy on 2009-09-07
Ohh,

When I set the stack layout on curved GUI it works but otherwise it won't show anything by left clicking.

Guess this is a flaw.

---

