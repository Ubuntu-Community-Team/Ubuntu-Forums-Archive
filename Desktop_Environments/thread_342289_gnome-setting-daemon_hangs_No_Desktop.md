---
title: "gnome-setting-daemon hangs No Desktop"
date: 2007-01-19
forum: Desktop Environments
---

### Post by fokuslee on 2007-01-19
This happened all of a sudden, i can only get in failsafe gnome now.  
when i try to mannually start gnome-settings-daemon i get this

(gnome-settings-daemon:4808): GSwitchIt-WARNING **: Unable to connect to dbus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

** (gnome-settings-daemon:4808): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:4808): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:4808): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (bug-buddy:4814): WARNING **: Couldn't load icon for Open Folder
fokuslee@fokuslee-ubuntu:~$ 

plz help
ps i tried reinstalling dbus no luck there.  aye.

---

### Post by kalyugi on 2007-01-19
let me know what happened mate

---

### Post by benndamann33 on 2007-02-18
yeah, how'd you ffix

---

