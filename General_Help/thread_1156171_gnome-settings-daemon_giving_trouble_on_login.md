---
title: "gnome-settings-daemon giving trouble on login"
date: 2009-05-11
forum: General Help
---

### Post by 4t0m1c_w07f on 2009-05-11
Hi guys
I updated to 9.04 last week and completed all the necesary updates and since the updates when i login it says that theres a problem with the gnome-settings-daemon

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

and this is the output in the terminal:

```
jared@4t0m1c_w07f:~$ gnome-settings-daemon 

(gnome-settings-daemon:7052): GLib-GObject-WARNING **: cannot register existing type `GstRTPMux'

(gnome-settings-daemon:7052): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
```

---

### Post by 4t0m1c_w07f on 2009-05-11
bump

---

### Post by kerry_s on 2009-05-11
check the session, see if it's even in the startup programs, if it's not add it.

---

### Post by 4t0m1c_w07f on 2009-05-12
It's there... It attempts to load it then crashes...

---

### Post by 4t0m1c_w07f on 2009-05-18
please need help on this urgent matter... :frown:

---

