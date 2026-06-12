---
title: "reset evolution-data-server?"
date: 2006-01-06
forum: General Help
---

### Post by vijay750 on 2006-01-06
Hello.

I'm having trouble with displaying calendar info in evolution on breezy. Things were working well, until I installed beagle. Subsequently, I'm unable to see any events on the personal calendar. Adding new events happens without any errors, but they too don't show up. I suspect that its something to do with the interaction of evolution-data-server, beagle, and evolution, but I am not able to figure out what exactly. Any pointers?

If I try to remove my ~/.evolution directory, to recreate the data, it doesn't work - when I restart evolution, the .evolution directory is created with data cached from somewhere. Is this because evolution-data-server keeps the data in memory somewhere? If so, how can I reset my evolution data?

These are the error messages from evolution:
(evolution:16115): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:16115): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:16115): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:16115): Gtk-CRITICAL **: gtk_tree_sortable_set_sort_column_id: assertion `GTK_IS_TREE_SORTABLE (sortable)' failed

(evolution:16115): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(evolution:16115): e-utils-WARNING **: Cannot resolve symbol 'org_gnome_new_mail_config' in plugin '/usr/lib/evolution/2.4/plugins/liborg-gnome-new-mail-notify.so' (not exported?)
BBDB spinning up...

(evolution:16115): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

TIA,
Vijay

---

