---
title: "rhythmbox crashes once every 5 runs"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Mandeep on 2006-08-31
every so often ill open rhythmbox just to have it crash immediately. ill click on restart application and when it reloads it crashes again. i finally caught the error in terminal and this is what i get [http://paste.ubuntu-nl.org/22193](http://paste.ubuntu-nl.org/22193) i was wondering if some1 knew what causes this.

---

### Post by aysiu on 2006-09-01
So you get this? ```
(rhythmbox:19151): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_get_mode: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_get_mode: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_get_mode: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:19151): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:19151): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
``` Unfortunately, [it doesn't look to be a very common error](http://www.google.com/search?hl=en&q=GLib-GObject-WARNING+**%3A+instance+of+invalid+non-instantiatable+type+%60%28null%29%27&btnG=Google+Search).

Has it always been like this, or did it happen after a certain event?

Have you tried creating a new user and seeing if this test user gets the same error?

---

