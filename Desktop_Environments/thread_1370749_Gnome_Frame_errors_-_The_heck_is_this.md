---
title: "Gnome Frame errors - The heck is this?"
date: 2010-01-02
forum: Desktop Environments
---

### Post by joebrueske on 2010-01-02
I did a search on the Glib-GObject error string, and I think it's an internal gnome error that can't be fixed on how it manages its internal children. If I'm wrong and someone has a suggestion on how to fix this, COOL.

Upon opening window:
```
** (gedit:24630): WARNING **: Cannot extract frame (0, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (36, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (72, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (108, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (144, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (180, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (216, 0) from the grid
** (gedit:24630): WARNING **: Cannot extract frame (252, 0) from the grid

```

After closing Window:
```

(gedit:24630): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
(gedit:24630): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
(gedit:24630): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
```

---

