---
title: "gnome libglade warning error"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Elyseum on 2005-04-15
When i want to add my printer i get this error:

> ** (gnome-cups-add:8896): WARNING **: failed request with status 1030

(gnome-cups-add:8896): libglade-WARNING **: could not find `gnome' init function: `glade_module_register_widgets': /usr/lib/libgmodule-2.0.so.0: undefined symbol: glade_module_register_widgets

(gnome-cups-add:8896): libglade-WARNING **: unknown widget class 'GnomeDruid'

(gnome-cups-add:8896): GLib-GObject-WARNING **: gsignal.c:1716: signal `cancel' is invalid for instance `0x80fe0b0'

** (gnome-cups-add:8896): WARNING **: unknown page connection_page


** (gnome-cups-add:8896): WARNING **: unknown page driver_page


How do i solve this?

---

### Post by Elyseum on 2005-04-17
up


Anybody knows the command to let ubuntu look for my printer without a window then?

---

### Post by Elyseum on 2005-05-03
nobody?

---

### Post by shakin on 2005-05-03
I used kcontrol. It has a very good wizard to add a printer. You'll need the kde libraries installed, but those could be useful for other programs as well.

---

### Post by Elyseum on 2005-05-04
** (process:8688): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:8688): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:8688): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

I get this error when installing kcontrol, i got it when installing some other things too, how do i solve this?

---

