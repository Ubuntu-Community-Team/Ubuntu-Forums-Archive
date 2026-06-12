---
title: "Assertion errors with Nautilus"
date: 2012-09-23
forum: Desktop Environments
---

### Post by Peregrino69 on 2012-09-23
Hi all

I sudoed Nautilus to copy some backgrounds to /usr/share/backgrounds. Copy goes OK,  but I get these errors on command line:

```
(nautilus:3008): Gtk-CRITICAL **: gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed

(nautilus:3008): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(nautilus:2673): Gtk-CRITICAL **: gtk_action_set_sensitive: assertion `GTK_IS_ACTION (action)' failed 
```I googled this, found a few similar bug reports. Anyone have any idea, or should I report this somewhere?

Cheers,
P

---

