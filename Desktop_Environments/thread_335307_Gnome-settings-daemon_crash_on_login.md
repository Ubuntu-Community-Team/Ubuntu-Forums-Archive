---
title: "Gnome-settings-daemon crash on login"
date: 2007-01-10
forum: Desktop Environments
---

### Post by shrimphead on 2007-01-10
Hi all

I'm having a problem with gnome-settings-daemon. It started when I tried to open the gnome themer to change my icon theme from within an XGL session running beryl.

As soon as the themer opened Gnome locked up and I was forced to ctrl-alt-backspace my X session. Now every time I start Gnome I get a dialog saying Gnome-settings-daemon cannot be started due to a timeout and the rest of Gnome loads my default settings.

If I try to start the daemon manually it locks up my session and I have to ctrl-alt-backspace it again. I can't find anything in the log files anywhere pointing at gnome-settings-daemon. I managed to get a dbus trace by logging into a failsafe terminal and running it from there. output is as follows:

```
(no debugging symbols found)
[New Thread -1228379232 (LWP 7074)]

(gnome-settings-daemon:7068): GSwitchIt-WARNING **: Unable to connect to dbus: Unable to determine the address of the message bus (try ‘man dbus-launch’ and ‘man dbus-daemon’ for help)

** (gnome-settings-daemon:7068): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL’ failed

** (gnome-settings-daemon:7068): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL’ failed

** (gnome-settings-daemon:7068): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)’ failed

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1226680656 (LWP 7068)]
0×0806915d in keyboard_config_registry_get_type ()
```

I notice it seems to be a problem relating to dBus but I'm out of ideas on how to fix it. I'd really appreciate the help if possible :)

thanks in advance

---

### Post by play0r on 2007-01-10
you may want to try & reinstall the dbus packages.

```
sudo apt-get install dbus*
```

ez,
play0r

---

### Post by shrimphead on 2007-01-15
fixed this issue, it was purely my fault :( I had installed the redhat-artwork rpm using alien so I could use the bluecurve icon set, something buggered up resulting in gnome-settings-daemon crashing everytime it tried to load my icon theme.

fixed by extracting the icons from the rpm manually and dumping them in ~/.icons

---

