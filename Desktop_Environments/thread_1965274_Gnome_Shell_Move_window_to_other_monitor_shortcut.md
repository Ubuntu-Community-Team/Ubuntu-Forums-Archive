---
title: "Gnome Shell Move window to other monitor shortcut"
date: 2012-04-25
forum: Desktop Environments
---

### Post by irvingswiftj86 on 2012-04-25
Hi,

I am running Gnome Shell (3.3) on my 11.10 version of ubuntu with Dual Monitors, my question is:
Is there a keyboard shortcut to move a window from one monitor to the other?

I couldn't see it in the list of shortcuts, is there an application that could do this for me?

Cheers:KS

---

### Post by codingman on 2012-04-25
I thought you could just drag it. No?

---

### Post by markbl on 2012-04-25
> **irvingswiftj86 said:**
> I couldn't see it in the list of shortcuts, is there an application that could do this for me?
If you are a programmer then it would not be hard to modify [https://github.com/paulswartz/gnome-shell-grid](https://github.com/paulswartz/gnome-shell-grid) to do what you want.

---

### Post by irvingswiftj86 on 2012-04-26
codingman: Any excuse not to use the mouse! I like to use it as little as possible.

markbl: That is fantastic, I will have a crack at that. :-)

---

### Post by cho1Ohlu on 2012-12-24
Following is a crude hack of the above script. It removes some code I don't need, but it is less elegant and less correct. It assumes 2 monitors aligned horizontally with the same horizontal resolution. Works for me for gnome-shell, might not work for you. 

```
#!/usr/bin/env python
import Xlib.display, gtk
from Xlib import X, XK
import wnck

# Ctrl-Alt-Shift
KEY_MODIFIER_MASK = X.Mod1Mask | X.ControlMask | X.ShiftMask 

display = Xlib.display.Display()
root = display.screen().root
root.change_attributes(event_mask = X.KeyReleaseMask)
screen = wnck.screen_get_default()
screen.force_update()

# register keys and modifiers
for keysym in [XK.XK_Right, XK.XK_Left]:
    root.grab_key(display.keysym_to_keycode(keysym), KEY_MODIFIER_MASK, 
            True, X.GrabModeAsync, X.GrabModeAsync)

while True:
    # Needed for correct window selection
    while gtk.events_pending():
        gtk.main_iteration()
    event = root.display.next_event()
    if event.type == X.KeyRelease:
        win = screen.get_active_window()
        x, y, w, h = pos = win.get_geometry()
        keysym = display.keycode_to_keysym(event.detail, 0)
        if keysym == XK.XK_Right:
            if x+screen.get_width()/2 < screen.get_width():
                x += screen.get_width()/2
        elif keysym == XK.XK_Left:
            if x-screen.get_width()/2 >= 0:
                x -= screen.get_width()/2
        else:
            continue
        win.set_geometry(0, 3, x-4, y-25, w, h)
```

---

### Post by toobaz on 2013-12-10
This extension perfectly solves the problem:
[https://extensions.gnome.org/extension/39/put-windows/](https://extensions.gnome.org/extension/39/put-windows/)

---

### Post by oldos2er on 2013-12-10
Old thread closed.

---

