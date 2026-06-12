---
title: "Make gtk apps look like qt (KDE) - any idea?"
date: 2005-10-06
forum: Desktop Environments
---

### Post by daller on 2005-10-06
Hi There,

I would like all gtk apps (gnome) to look like qt (KDE)

I installed "gtk2-engines-gtk-qt" - but it doesn't seem to have helped (I even restarted)

Does it need some sort of configuration?

Examples of apps, not looking that good in KDE:

Gimp
Anjuta
aMule
xMule
Firefox

etc...

Any ideas?

---

### Post by Manny C on 2005-10-06
Firefox is [themeable]("https://addons.mozilla.org/themes/moreinfo.php?id=916"). 

The rest i am not sure about.

---

### Post by f1dave on 2005-10-06
Does a section like "GTK Appearance" or similar appear in your kcontrol?

---

### Post by daller on 2005-10-06
It looks like this: (attached)

---

### Post by f1dave on 2005-10-06
Yep... and there should be some styles in that drop down box to choose from...

---

### Post by !nkubus on 2005-10-06
Yeah you should see Gtk Fonts and style in you kControl... even if it's selected, choose something else in the fonts and in the style parts. save it and reselect "make my  gtk apps look like kde ones" and the same with the fonts. 

and you should be fine

hope it helps

---

### Post by Gárgula on 2005-10-06
When I install this package my firefox stop work.

--
(Gecko:10247): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' failed

(Gecko:10247): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `src != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(Gecko:10247): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:10247): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

Falha de segmentação

--

Any idea? :confused:

---

### Post by daller on 2005-10-06
It almost worked... The ugly GTK-standard is gone!!!

But what about the icons?

---

### Post by !nkubus on 2005-10-06
The Icons is are not changing at the moment. I hope in a near future it will be done :)

---

