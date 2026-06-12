---
title: "Hopefully a simple solution to a missing GNOME panel"
date: 2007-07-05
forum: Desktop Environments
---

### Post by BVStang1967 on 2007-07-05
Well I installed Kibadock messed around with it and decided I wanted my Gnome lower panel back so I opened up the terminal and typed

sudo gnome-panel

(and I get this)

(gnome-panel:6176): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -12 and height 24

Now my panel is back but once I close my terminal window the panel goes with it.
But thats not all there is a pop window that says

I've detected a panel already running, and will now exit; and no matter how many times I close the popup it comes back.

What to do?

---

### Post by x1a4 on 2007-07-05
Don't run it using sudo, and fork it away from the terminal.

```
gnome-panel &
```

should do the trick.  Or, run gnome-panel (no '&') from the Run dialog (Alt+F2).

---

### Post by BVStang1967 on 2007-07-06
When I try what you said I get the pop up window saying there is already another panel running... should I delete the panel on top too, and then try that command?

---

### Post by BVStang1967 on 2007-07-06
Nevermind everybody, I just made a new panel with all the same features. 
(I didn't know I could do that, still a newbie)

---

