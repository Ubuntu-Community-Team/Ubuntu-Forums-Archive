---
title: "GNOME/Bonobo apps taking a long time to load"
date: 2005-06-16
forum: Desktop Environments
---

### Post by darthsabbath on 2005-06-16
Hey all,

Been having an issue on my notebook machine recently that I can't figure out, nor find anything on.  Basically, when I try and open, say, Gedit or the System Resources applet, it takes literally 3-4 minutes to open.  Apps like Firefox work fine.  

When I try and start from the command prompt, it just sits there until the app opens.  Here's the tail end of my .xsession-errors log from the last time I opened Gedit...

```
** (gedit:14699): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:14699): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:14699): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:14699): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:14699): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:14699): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:14699): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:14699): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:14699): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:14699): CRITICAL **: gedit_file_new: assertion `ret != FALSE' failed

```

If I try to kill the gnome-panel or restart GDM, my desktop won't return until I restart the computer.

This seems to happen intermittently, with no pattern that I've noticed. :/

If I need to provide any more info, please let me know.

Phil

---

