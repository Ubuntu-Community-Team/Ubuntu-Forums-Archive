---
title: "Gimp crashes in Maverick"
date: 2011-04-09
forum: Desktop Environments
---

### Post by SwedishWings on 2011-04-09
Dear community,

Since installing Maverick i have issues with Gimp. If i have several documents loaded and click the "Close button" on any of them, gimp crashes with the following:

```
mike@mike-laptop:~/Desktop$ gimp
0.157480, 0.202990, 0.164268
0.231007, 0.196103, 0.277870

(gimp:3255): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gimp:3255): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gimp:3255): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gimp:3255): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gimp:3255): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gimp:3255): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gimp:3255): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gimp:3255): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gimp:3255): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(gimp:3255): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gimp:3255): GLib-GObject-WARNING **: invalid uninstantiatable type `<unknown>' in cast to `GObject'

(gimp:3255): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

[B](script-fu:3260): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault[/B]

```

Has anyone else experienced this? Is there a workaround?

Thanks in advance,
Mike

---

