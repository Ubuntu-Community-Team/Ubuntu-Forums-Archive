---
title: "gksudo taking long time to load apps"
date: 2005-12-10
forum: Desktop Environments
---

### Post by royg1234 on 2005-12-10
hey.  Whenever I do, for example

```
sudo gedit text.txt
```

it takes *forever* for gedit to open.  anybody know what to do about this?

---

### Post by royg1234 on 2005-12-10
more info.  It doesn't even open gedit.  Here's what terminal says after a while.

```

roy@roylaptop:~/ipw2200-1.0.6$ sudo gedit /etc/wpa_supplicant.conf

** (gedit:9345): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed

(gedit:9345): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:9345): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_MDI (mdi)' failed

(gedit:9345): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:9345): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:9345): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDOW (win)' failed

** (gedit:9345): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9345): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9345): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:9345): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:9345): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:9345): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:9345): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
roy@roylaptop:~/ipw2200-1.0.6$


```

---

### Post by aysiu on 2005-12-10
What about ```
gksudo gedit text
``` or ```
sudo nano text
```?

---

### Post by mustang on 2005-12-10
gEdit usually takes awhile the load in general. I think I might start using pico/nano as suggested above.

If you want something that resembles notepad (in windows) and loads quick too, get mousepad

```
sudo apt-get install mousepad
```

---

### Post by arnieboy on 2005-12-10
[QUOTE=royg1234]hey.  Whenever I do, for example

```
sudo gedit text.txt
```

it takes *forever* for gedit to open.  anybody know what to do about this?[/QUOTE]
change your desktop theme to "human" and check again.

---

