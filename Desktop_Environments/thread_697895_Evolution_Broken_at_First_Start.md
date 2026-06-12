---
title: "Evolution Broken at First Start"
date: 2008-02-15
forum: Desktop Environments
---

### Post by hgurol on 2008-02-15
Hi,

I have just installed Ubuntu yesterday. And when I tried to launch the Evolution for the first time, it didnt start. Below is the error message I get, when I try to start it from the terminal.

I have also tried to remove and re-install Evolution with the "apt-get remove" and "apt-get purge" but neither the problem nor the error message has changed.

Any suggestions ?

```

hgurol@hubuntu:~$ evolution --component=mail
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin

(evolution:6198): XML-CRITICAL **: AttValue: ' expected


(evolution:6198): XML-CRITICAL **: attributes construct error


(evolution:6198): XML-CRITICAL **: Couldn't find end of Start Tag property line 3498


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3494


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3493


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3488


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3487


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3457


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3456


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3450


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3449


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 253


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 252


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 237


(evolution:6198): XML-CRITICAL **: Premature end of data in tag glade-interface line 4


(evolution:6198): libglade-WARNING **: widget_depth != 0 (6)

(evolution:6198): libglade-WARNING **: did not finish in PARSER_FINISH state

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_show_all: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(evolution:6198): GnomeUI-CRITICAL **: gnome_druid_append_page: assertion `page != NULL' failed

(evolution:6198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:6198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:6198): XML-CRITICAL **: AttValue: ' expected


(evolution:6198): XML-CRITICAL **: attributes construct error


(evolution:6198): XML-CRITICAL **: Couldn't find end of Start Tag property line 3498


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3494


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3493


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3488


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3487


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3457


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3456


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3450


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3449


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 253


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 252


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 237


(evolution:6198): XML-CRITICAL **: Premature end of data in tag glade-interface line 4


(evolution:6198): libglade-WARNING **: widget_depth != 0 (6)

(evolution:6198): libglade-WARNING **: did not finish in PARSER_FINISH state

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(evolution:6198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:6198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(evolution:6198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:6198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(evolution:6198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:6198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(evolution:6198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:6198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(evolution:6198): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:6198): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): Gtk-CRITICAL **: gtk_toggle_button_set_active: assertion `GTK_IS_TOGGLE_BUTTON (toggle_button)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(evolution:6198): XML-CRITICAL **: AttValue: ' expected


(evolution:6198): XML-CRITICAL **: attributes construct error


(evolution:6198): XML-CRITICAL **: Couldn't find end of Start Tag property line 3498


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3494


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3493


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3488


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3487


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3457


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3456


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 3450


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 3449


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 253


(evolution:6198): XML-CRITICAL **: Premature end of data in tag child line 252


(evolution:6198): XML-CRITICAL **: Premature end of data in tag widget line 237


(evolution:6198): XML-CRITICAL **: Premature end of data in tag glade-interface line 4


(evolution:6198): libglade-WARNING **: widget_depth != 0 (6)

(evolution:6198): libglade-WARNING **: did not finish in PARSER_FINISH state

(evolution:6198): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed
Segmentation fault (core dumped)
hgurol@hubuntu:~$ 



```

---

### Post by hgurol on 2008-02-16
I believe I have posted this on the wrong section of the forum.

Can a mod move this post to the correct section please?

Thank you....

---

