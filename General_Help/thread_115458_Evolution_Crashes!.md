---
title: "Evolution Crashes!"
date: 2006-01-10
forum: General Help
---

### Post by thermopyl on 2006-01-10
Hi
When i boot evolution it crashes when i go into the calendar. Can anyone give me any pointers on how i can 'revive' it? I have tried reinstalling with no luck!

The error message in the console is:

(evolution:19964): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:19964): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:19964): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:19964): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x857af30'

(evolution:19964): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x857af30'

(evolution:19964): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:19964): calendar-gui-WARNING **: e-cal-model.c:1487: Unable to get qu ery

(evolution:19964): calendar-gui-WARNING **: e-cal-model.c:1487: Unable to get qu ery

(evolution:19964): calendar-gui-WARNING **: e-cal-model.c:1487: Unable to get qu ery

(evolution:19964): calendar-gui-WARNING **: e-cal-model.c:1487: Unable to get qu ery

(evolution:19964): calendar-gui-WARNING **: e-cal-model.c:1487: Unable to get qu ery

(evolution:19964): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:19964): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x85c5c00'

(evolution:19964): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x85c5c00'

(evolution:19964): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x85c5c00'

---

### Post by magnusbb on 2006-01-10
Which version of Evolution is this?

---

### Post by spiregrain on 2006-01-10
I had a similar problem when using Evolution with some hacked-up Cairo-enhanced theme engine.

I suggest you try it again with a really simple theme, say  "Traditional".

---

### Post by thermopyl on 2006-01-10
evolution 2.4.1...

---

### Post by thermopyl on 2006-01-10
[QUOTE=spiregrain]I had a similar problem when using Evolution with some hacked-up Cairo-enhanced theme engine.

I suggest you try it again with a really simple theme, say  "Traditional".[/QUOTE]

hmmm... i am using perfection theme...i have tried to revert to the default Human theme (i know it worked originally!), but i get the same problem

do you think i would have to uninstall cairo/clearlooks?

---

### Post by spiregrain on 2006-01-10
Not sure.  I've got the Cairo backend builtin to some of my themes (Humand and Clearlooks included I think) but following instructions in some forum.  That might not be the cause of the problem, but  I found that switching to "Traditional" at the bottom of the list got it working problem.

---

### Post by spiregrain on 2006-01-10
Here's what happens.  The first time it crashes, and the second time it doesn't:

```
ken@franklin ~ $ evolution
adding hook target 'source'

(evolution:8353): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:8353): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC(gc)' failed

(evolution:8353): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC(gc)' failed

(evolution:8353): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' isinvalid for instance `0x81cd260'

(evolution:8353): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' isinvalid for instance `0x81cd260'
ken@franklin ~ $ # here I switched theme
ken@franklin ~ $ # to traditional
ken@franklin ~ $ evolution
adding hook target 'source'

(evolution:8375): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:8375): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:8375): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:8375): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:8375): GnomeCanvas-CRITICAL **: gnome_canvas_request_redraw: assertion `GNOME_IS_CANVAS (canvas)' failed

(evolution:8375): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed
ken@franklin ~ $ # it says "failed" there, but it didn't crash

```

---

### Post by thermopyl on 2006-01-10
interesting...

if i change to Traditional or any other theme other than Human or a Clearlooks theme then, like you, no problems.

If i go into the Theme Details I can select the icons and window borders from the clearlooks themes as soon as i apply the controls....crash!

This would suggest some issue in the clearlooks components...is this something that can be updated via apt-get etc?

---

