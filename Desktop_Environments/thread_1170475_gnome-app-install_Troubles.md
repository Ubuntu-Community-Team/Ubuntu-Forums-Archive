---
title: "gnome-app-install Troubles"
date: 2009-05-26
forum: Desktop Environments
---

### Post by GandalphCerebrum on 2009-05-26
Hello,       When I try to use the Add/Remove Applications tool, it crashes immediately on selecting anything. I have tried reinstalling the package gnome-app-install from both Synaptic and apt-get, but it did not fix anything.    The output in the terminal when I run gnome-app install is this:   ** (gnome-app-install:17782): WARNING **: return value of custom widget handler was not a GtkWidget /usr/lib/python2.6/dist-packages/AppInstall/AppInstall.py:1295: GtkWarning: gtk_tree_model_sort_set_sort_column_id: assertion `tree_model_sort->default_sort_func != NULL' failed   item.applications.set_sort_column_id(-1, sort_type)    So yeah, does anyone know what is going on here, or how to fix it?

---

