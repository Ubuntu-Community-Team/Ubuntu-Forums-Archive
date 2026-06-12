---
title: "gedit &amp; User manager &amp; Service manager - Strange behaviors"
date: 2005-10-17
forum: Desktop Environments
---

### Post by guimou on 2005-10-17
Hi,

I just upgraded from Hoary to Breezy. Well, in fact clean upgrade = new install, only keep data partitions.
I experience a strange behavior with gedit as it sometimes works... sometimes does not...
From a console: "gedit" (or "sudo gedit" for config files) works Ok for a while but then, without doing anything specific, when I try again, the same commands just freeze (blinking cursor only) and nothing happens...
I also have something that can be related: I tried to open the user/group and the manager. One time it worked perfectly, the other, nothing happened... but after a few minutes it just opened. Same thing for the services manager...

Anyone an idea of what could be happening?
Thanks.

---

### Post by guimou on 2005-10-17
One precision after some tests. If I leave my command "sudo gedit" running long enough, I got this messages:

---------
** (gedit:9912): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9912): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9912): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9912): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:9912): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:9912): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:9912): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:9912): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:9912): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:9912): CRITICAL **: gedit_file_new: assertion `ret != FALSE' failed
--------

Anyone knows what to do with it? Thanks.

---

### Post by flipkick on 2005-10-17
try to change your sudo/root password.

type "passwd" in the console and follow instructions. worked for me.

---

### Post by guimou on 2005-10-18
Thanks for the try, but that's not working.
Exactly the same error...

Someone else any idea?

---

