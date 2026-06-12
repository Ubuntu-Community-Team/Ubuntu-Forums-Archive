---
title: "Update Manager Problem"
date: 2005-12-02
forum: Desktop Environments
---

### Post by Greeface on 2005-12-02
When I try to install the updates from the update manager it starts to download the files then immediately stops.  If I hit 'Install' again it does the same thing.  When I ran it from the terminal it came up like this:
```
greg@Computer:~$ sudo update-manager
Password:
Reading package lists... Done
Building dependency tree... Done

(synaptic:9378): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9378): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Reading package lists... Done
Building dependency tree... Done
```

Any ideas on how to fix this?

---

### Post by teaker1s on 2005-12-02
mine did similar when I installed another desktop, I sorted mine by changing the upgrade type several times and hit refresh each time seems to clear the cache and it's been fine ever since.

---

