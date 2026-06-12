---
title: "disable compiz effect for notify-osd"
date: 2009-05-06
forum: Desktop Environments
---

### Post by tomcheng76 on 2009-05-06
Hi
I turned on animation effect (random) in ccsm.
How to grab the window class/window id/window title so that i can add notify-osd to the exception list in animation setting of ccsm?
It just disappear so fast!
Thanks:)

---

### Post by tomcheng76 on 2009-05-07
found in src/bubble.c...
```

        /*  "clear" input-mask, set title/icon/attributes */
        gtk_widget_set_app_paintable (window, TRUE);
        gtk_window_set_title (GTK_WINDOW (window), "notify-osd");
        gtk_window_set_decorated (GTK_WINDOW (window), FALSE);
        gtk_window_set_keep_above (GTK_WINDOW (window), TRUE);
        gtk_window_set_resizable (GTK_WINDOW (window), FALSE);
        gtk_window_set_accept_focus (GTK_WINDOW (window), FALSE);
        gtk_window_set_opacity (GTK_WINDOW (window), 0.0f);

```
title is "notify-osd" and it doesn't accept focus, so ccsm cant grab it.

---

