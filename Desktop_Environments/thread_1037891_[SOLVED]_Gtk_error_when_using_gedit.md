---
title: "[SOLVED] Gtk error when using gedit"
date: 2009-01-12
forum: Desktop Environments
---

### Post by SamNSane on 2009-01-12
During the past week one of the three Hardy Heron boxes I use has started displaying a peculiar symptom. When I launch gedit on this system the application's window pops up promptly as expected, but then the application becomes non-responsive. The window "grays out" for a while and then returns to normal appearance. Then when I proceed to open a file in gedit the same behavior is repeated. All this time the HD is thrashing like mad.

I am able to do other tasks on the system, though they are slowed down a little.

I can launch the system monitor or TOP when this happens. I can see that gedit is using anywhere from 40% to almost 90% of CPU cycles. If the application is left alone long enough -- several minutes -- it usually starts responding normally.

If I launch gedit from within a terminal window I get no error messages at the startup of the application, but I do see this error message in the terminal after closing gedit:

```

GtkSourceView-Message: gtksourceundomanager.c:1113: oops

```

The system is fully up-to-date with standard repositories plus backport enabled.

Has anyone else seen this issue? Does anyone have an idea as to how I might rectify it? I have already removed and then reinstalled gedit to see if that would make a difference. It didn't. I'm a little less easy about pulling the same maneuver with the gtk packages, so I haven't tried anything like that as of yet.

---

### Post by SamNSane on 2009-01-12
The System log also contains these error messages:

```

Jan 12 07:42:42 rawbuntu gdmgreeter[5733]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
Jan 12 07:42:42 rawbuntu gdmgreeter[5733]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed
Jan 12 07:42:42 rawbuntu gdmgreeter[5733]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed
Jan 12 07:42:42 rawbuntu gdmgreeter[5733]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

```

---

### Post by SamNSane on 2009-01-12
Okay, I'll stop talking to myself. I guess the problem is solved. I went into gconf-editor to look at the settings for gedit. The virtual root setting for gedit-2/plugins/filebrowser/on_load had been set to a location under /var. I have no idea how that happened. But once I set it to file:///home/user/ the editor's functionality reverted to normal.

Do I get to thank myself?

Nah! I should spank myself -- for wasting the time of people who read this thread.

Moron signing out.

---

