---
title: "Pidgin fails"
date: 2009-01-04
forum: General Help
---

### Post by bonfire89 on 2009-01-04
Hi,

(this isn't an urgent matter for me, I just thought that I would report it)

Pidgin started exiting randomly, I can't even recall making any system changes.

I decided to run pidgin through the terminal and sometime between opening and failing... I suspect at the same time as failing this appeared in the terminal window.

```

$ pidgin

(pidgin:8173): GStreamer-CRITICAL **:
Trying to dispose element test, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

```



edit:


so, I ran pidgin again via the cmd line and got a different error

```

$ pidgin

(pidgin:15222): GStreamer-CRITICAL **:
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:15222): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:15222): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:15222): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:15222): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:15222): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:15222): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:15222): GStreamer-CRITICAL **:
Trying to dispose element test, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

Segmentation fault

```

---

