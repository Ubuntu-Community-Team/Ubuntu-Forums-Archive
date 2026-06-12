---
title: "Pychess crashing Ubuntu 10.10"
date: 2010-10-16
forum: Gaming &amp; Leisure
---

### Post by Zteam on 2010-10-16
Hello!

I use to play chess, with pychess sometimes, this has always worked great.

But since I updated to 10.10 the game crashes if I try to to close the game and start a new one, very annoying...

This problems never existed in Ubuntu 10.04.

---

### Post by PC_load_letter on 2010-10-16
start it from terminal by typing 
```
pychess
```
then post the output here (when it crashes).

---

### Post by lucasart on 2010-10-24
> **PC_load_letter said:**
> start it from terminal by typing 
```
pychess
```then post the output here (when it crashes).

** Message: pygobject_register_sinkfunc is deprecated (GstObject)
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:438: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_object_newv: object class `GtkWindow' has no property named `adjustment'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_object_newv: object class `GtkWindow' has no property named `climb_rate'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:438: Warning: g_value_transform: assertion `G_IS_VALUE (src_value)' failed
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:438: Warning: unable to set property `climb-rate' of type `gdouble' from value of type `(null)'
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_param_spec_pool_lookup: assertion `param_name != NULL' failed
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_object_newv: object class `GtkWindow' has no property named `(null)'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_value_transform: assertion `G_IS_VALUE (src_value)' failed
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: unable to set property `can-focus' of type `gboolean' from value of type `(null)'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
lucas@lucas-desktop:~$ pychess > toto.txt
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:438: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_object_newv: object class `GtkWindow' has no property named `adjustment'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_object_newv: object class `GtkWindow' has no property named `climb_rate'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:438: Warning: g_value_transform: assertion `G_IS_VALUE (src_value)' failed
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_param_spec_pool_lookup: assertion `param_name != NULL' failed
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:438: Warning: unable to set property `climb-rate' of type `gdouble' from value of type `(null)'
  self.glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_object_newv: object class `GtkWindow' has no property named `(null)'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: g_value_transform: assertion `G_IS_VALUE (src_value)' failed
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/System/uistuff.py:420: Warning: unable to set property `can-focus' of type `gboolean' from value of type `(null)'
  glade = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
/usr/local/lib/python2.6/dist-packages/pychess/ic/ICLounge.py:267: DeprecationWarning: Use the new widget gtk.Tooltip
  gtk.Tooltips().set_tip(expander, title)
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamenanny.py", line 159, in game_ended
    gmwidg.showMessage(md)
  File "/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py", line 260, in showMessage
    message, separator, hbuttonbox = messageDialog.child.get_children()
ValueError: need more than 2 values to unpack
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:349: GtkWarning: gtk_box_pack: assertion `child->parent == NULL' failed
  centerVBox.pack_start(notebooks["messageArea"], expand=False)
/usr/local/lib/python2.6/dist-packages/pychess/widgets/pydock/PyDockLeaf.py:62: GtkWarning: Can't set a parent on widget which has a parent

  self.book.append_page(widget, title)
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:449: GtkWarning: gtk_box_pack: assertion `child->parent == NULL' failed
  centerVBox.pack_start(notebooks["statusbar"], expand=False)
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:451: GtkWarning: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
  centerVBox.show_all()
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:451: GtkWarning: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed
  centerVBox.show_all()
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:496: GtkWarning: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
  notebooks[panel.__name__].append_page(instance)
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:496: GtkWarning: gdk_window_show_internal: assertion `GDK_IS_WINDOW (window)' failed
  notebooks[panel.__name__].append_page(instance)
/usr/local/lib/python2.6/dist-packages/pychess/widgets/gamewidget.py:496: GtkWarning: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed
  notebooks[panel.__name__].append_page(instance)
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:8828:gtk_widget_real_map: assertion failed: (gtk_widget_get_realized (widget))

---

### Post by urmomsgoat on 2010-11-17
Please file a bug at _[http://code.google.com/p/pychess/issues/entry](http://code.google.com/p/pychess/issues/entry)_

Before you file the bug though, see if you can reproduce the bug with the latest released .deb from _[http://code.google.com/p/pychess/downloads/list](http://code.google.com/p/pychess/downloads/list)_ (currently pychess-0.10rc1-1) and also try deleting your previous config (rm -rf ~/.config/pychess).

---

