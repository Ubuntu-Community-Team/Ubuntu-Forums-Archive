---
title: "Gunrealtools GUTS, again...."
date: 2008-11-21
forum: Gaming &amp; Leisure
---

### Post by Eazy© on 2008-11-21
Hi!
I have trouble to run the cache manager in[ Gunrealtools]("http://gunrealtools.sourceforge.net/"). It segfaults as soon as I hit the cache manager button. Everything else works fine but not the cache manager (which is the only thing I use in this program). This is what I get in the console:
```
eazy@eazy-linux:~$ guts

(guts:23368): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(guts:23368): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gtype.c:3362: type id `0' is invalid

(guts:23368): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmenteringsfel
eazy@eazy-linux:~$
```
I have been using this program since Hoary, but since I installed Edgy, it just segfaults.

---

### Post by Vadi on 2008-11-21
It's outdated unfortunately. needs to be updated for gtk changes

---

