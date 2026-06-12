---
title: "Gimpshop Install error"
date: 2009-06-13
forum: General Help
---

### Post by msmarc on 2009-06-13
I'm trying to install gimpshop on my IMac G5 with Ubuntu 8.10 Intrepid. I tried installing the deb package from the Gimpshop site [http://www.gimpshop.com/download.shtml]("http://www.gimpshop.com/download.shtml") but it didn't work. I downloaded the source files and complied them on my computer with ./configure, make and make install. Everything worked until I ran the gimp command after I compiled everything. It took me through a gimp setup and afterward gave me this error:

(gimp:4718): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:4718): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:4718): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:4718): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:4718): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:4718): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:4718): GLib-GObject-WARNING **: cannot register existing type `GimpParamRGB'

(gimp:4718): GLib-GObject-CRITICAL **: g_param_spec_internal: assertion `G_TYPE_IS_PARAM (param_type) && param_type != G_TYPE_PARAM' failed
Segmentation fault

Any help appreciated

---

### Post by Dustin2128 on 2009-06-14
could you put it in between code tags? there's an annoying auto smiley thing that's screwing up your code.

---

### Post by Hobgoblin on 2009-06-14
```


(gimp:4718): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:4718): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:4718): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:4718): GLib-GObject-WARNING **: cannot register existing type `GimpConfigInterface'

(gimp:4718): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gimp:4718): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `g_type_parent (interface_type) == G_TYPE_INTERFACE' failed

(gimp:4718): GLib-GObject-WARNING **: cannot register existing type `GimpParamRGB'

(gimp:4718): GLib-GObject-CRITICAL **: g_param_spec_internal: assertion `G_TYPE_IS_PARAM (param_type) && param_type != G_TYPE_PARAM' failed
Segmentation fault

```

That help?

---

### Post by msmarc on 2009-06-14
Thanks for that I forgot to put it between the code tags!

---

