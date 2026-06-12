---
title: "Odd AWN Display"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by foo25 on 2007-12-23
Hey, been using Kubuntu for quite some time, but decided to switch over to Ubuntu yesterday. Anyway I seen AWN today and decided to try it out, but I'm quite confused as to why it's not working. When I run it from the console I get -

```
(avant-window-navigator:29636): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:29636): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed
```

Also when it does show up, it looks like this -

[IMG]http://i16.tinypic.com/6oy62dj.png[/IMG]

---

### Post by andrewsomething on 2007-12-23
Well, from the picture it would seem that you're not running a compositor. You need to have some sort of compositor running to use AWN, like Compiz or xcompmgr.

Also what version are you using? The up to date AWN will not even display with out a compositor and gives a better error that says you need a compositor. 

[http://wiki.awn-project.org/index.php?title=DistributionGuides#Ubuntu](http://wiki.awn-project.org/index.php?title=DistributionGuides#Ubuntu)

---

### Post by foo25 on 2007-12-23
Thanks for the quick reply. I actually installed AWN using that guide you provided, so I can only assume it's the latest version.

Ok, I seem to be getting somewhere, although now I've noticed that when an application is maximized, the icon disappears and the window stretches to the bottom of the screen, and when I run AWN I still receive the same error message -

[IMG]http://i14.tinypic.com/6lvq8hk.png[/IMG]

---

