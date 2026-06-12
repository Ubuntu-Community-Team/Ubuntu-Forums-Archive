---
title: "Nautilus crashes when clicking &quot;Computer&quot; Icon."
date: 2009-10-22
forum: Desktop Environments
---

### Post by neoideo on 2009-10-22
Nautilus crashes after attempting to open "Computer" Icon.
this is the error on console.

```

(nautilus:6043): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:6043): WARNING **: Got GFileInfo with NULL name in computer:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:6043): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```


is there any ay to repair it? i see is a Glib-GIO_CRITICAL error, 
i tried reinstalling libglib but the problem persists.

my ubuntu is 9.04 64-bit and i also have the version of 32-bit for gtk glib and related, is there a chance that nautilus is picking some libs form 32-bit and crashing? should i check some paths ?

---

