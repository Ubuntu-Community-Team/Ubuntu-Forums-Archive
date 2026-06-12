---
title: "Add/Remove programs Hosed."
date: 2009-06-03
forum: General Help
---

### Post by gdonwallace on 2009-06-03
Not sure what happened, but when I tried to run Add Remove programs this morning, I can see it trying to start up, but then nothing happens.

When I run sudo gnome-app-install from a terminal, it runs; but I get the following.

** (gnome-app-install:510): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1285: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
/usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_sort_column_id(-1, sort_type)

I thought that I was missing GtkWidget, but I am not running any widgets on my desktop.  So I am not sure what is messed up.

Any ideas?

thanks

---

### Post by gdonwallace on 2009-06-05
Not sure what happened, but after a reboot yesterday afternoon, add/remove programs started working fine.

Really odd.  The machine has only been up and running for 6 days.  

Just happy that its fixed.

---

