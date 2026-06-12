---
title: "Error when trying to start eclipse 3.4"
date: 2009-03-13
forum: General Help
---

### Post by RCholic on 2009-03-13
I followed this tutorial [http://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/](http://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/) to install eclipse 3.4 on my Ubuntu 8.10 server, however when I try to start eclipse, I got these errors:

```
(.:7530): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(.:7530): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(.:7530): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(.:7530): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(.:7530): GLib-GObject-WARNING **: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'

(.:7530): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(.:7530): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(.:7530): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(.:7530): Gdk-CRITICAL **: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(.:7530): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(.:7530): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(.:7530): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(.:7530): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(.:7530): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(.:7530): Pango-CRITICAL **: pango_layout_set_attributes: assertion `layout != NULL' failed

(.:7530): Pango-CRITICAL **: pango_layout_set_alignment: assertion `layout != NULL' failed

(.:7530): Pango-CRITICAL **: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed

(.:7530): Pango-CRITICAL **: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed

(.:7530): Pango-CRITICAL **: pango_layout_set_width: assertion `layout != NULL' failed

(.:7530): Pango-CRITICAL **: pango_layout_get_extents: assertion `layout != NULL' failed

(.:7530): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(.:7530): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(.:7530): Gtk-CRITICAL **: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed

(.:7530): Gtk-WARNING **: Invalid icon size 6
```

Eclipse3.4 is put in my /home folder.

I use java-6-sun-1.6.0.10.

What might be wrong? thanks

---

