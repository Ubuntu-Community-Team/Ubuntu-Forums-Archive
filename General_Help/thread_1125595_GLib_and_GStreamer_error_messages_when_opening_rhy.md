---
title: "GLib and GStreamer error messages when opening rhythmbox"
date: 2009-04-14
forum: General Help
---

### Post by acimmarusti on 2009-04-14
I opened rhythmbox on a terminal and then edited the tag of a newly added song and I got this mess of messages:

```


$ rhythmbox &

(rhythmbox-metadata:6661): GStreamer-CRITICAL **: gst_tag_get_type: assertion `info != NULL' failed

(rhythmbox-metadata:6661): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gtype.c:3940: type id `0' is invalid

(rhythmbox-metadata:6661): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced

(rhythmbox-metadata:6661): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gvalue.c:192: cannot initialize GValue with type `(null)', this type has no GTypeValueTable implementation

(rhythmbox-metadata:6661): GLib-GObject-CRITICAL **: g_value_transform: assertion `G_IS_VALUE (dest_value)' failed

(rhythmbox-metadata:6661): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed


```

Anyone know something? I didn't crash the program or anything. It works well still.

---

