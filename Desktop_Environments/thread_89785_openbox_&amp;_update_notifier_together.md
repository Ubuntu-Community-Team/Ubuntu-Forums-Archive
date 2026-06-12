---
title: "openbox &amp; update notifier together?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by anatole on 2005-11-13
hi,
i have a strange problem. i use openbox rather than gnome, but stil would like to use the update-notifier. the problem is, when i start it, i get:

```
attila@nanaki:~$ update-notifier 

** (update-notifier:9349): CRITICAL **: tray icon destroyed


** (update-notifier:9349): CRITICAL **: tray icon destroyed


(gnome_segv:9355): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gnome_segv:9355): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gnome_segv:9355): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gnome_segv:9355): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gnome_segv:9355): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(gnome_segv:9355): Gtk-WARNING **: Theme directory scalable/mimetypes of theme eXperienceCrystal has no size field
```

and a blank space blinks where the icon should be in the notification area (provided by docker) and then, the app exits. (the last warning line probably has nothing to do with the case.) any suggestions where should i start looking to get update-notifier work on openbox?

---

