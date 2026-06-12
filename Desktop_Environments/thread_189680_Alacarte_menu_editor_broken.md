---
title: "Alacarte menu editor broken"
date: 2006-06-05
forum: Desktop Environments
---

### Post by brettaw on 2006-06-05
Hi guys,

I've just switched from XP and am loving things so far. The only issue I have is with the menu editor.

I've installed a number of items through Synaptic, and the install finishes cleanly, but no icon appears in the menu. Upon opening Alacarte however the icon is there (and checked for display).

I've been messing around with this for hours. It seems random. I tried running Alacarte from the shell with output below

(alacarte:11296): GnomeUI-CRITICAL **: gnome_icon_selection_stop_loading: assertion `gis != NULL' failed
/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py:54: GtkWarning: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
  self.tree = gtk.glade.XML(

Any suggestions for a newbie :)

Thanks

---

