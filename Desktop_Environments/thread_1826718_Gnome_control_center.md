---
title: "Gnome control center"
date: 2011-08-16
forum: Desktop Environments
---

### Post by Z06Gal on 2011-08-16
Control center will not launch and when I try to start in via terminal, I get this output:



** (gnome-control-center:7957): WARNING **: 
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]


** (gnome-control-center:7957): WARNING **: 
error raised: [load_xbel_store: couldn't load bookmark file [NULL]
]


(gnome-control-center:7957): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-control-center:7957): GLib-CRITICAL **: g_strdelimit: assertion `string != NULL' failed

(gnome-control-center:7957): GLib-CRITICAL **: g_strrstr: assertion `haystack != NULL' failed

(gnome-control-center:7957): GLib-CRITICAL **: g_ascii_strdown: assertion `str != NULL' failed

(gnome-control-center:7957): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed
Segmentation fault


Anyone have any clue what this is?  Thank you in advance ;)


Robin

---

