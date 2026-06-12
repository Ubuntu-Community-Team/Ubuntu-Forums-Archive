---
title: "beagle still looking for old dbus libs"
date: 2005-10-16
forum: Desktop Environments
---

### Post by chapeaurouge on 2005-10-16
Hi all

I dist-upgraded today to breezy, and it's been going well, at 99%.

I tried beagle, but it is not working. It is still looking for an old version of dbus-sharp (dbus-1 package). That pkg was obsoleted by libdbus-1-1, dbus-1-utils and dbus. I removed it (with --purge), reinstalled it. Same with the dbus libs. Nothing does. Has anyone seen this pb?

```
beagled --fg --debug

** (/usr/local/lib/beagle/BeagleDaemon.exe:18396): WARNING **: The following assembly referenced from /usr/local/lib/beagle/BeagleDaemon.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=4)
     Version:    0.23.4.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/beagle).


** (/usr/local/lib/beagle/BeagleDaemon.exe:18396): WARNING **: The class DBus.DBusException could not be loaded, used in /usr/local/lib/beagle/BeagleDaemon.exe (token 0x01000049)

** (/usr/local/lib/beagle/BeagleDaemon.exe:18396): WARNING **: The class DBus.DBusException could not be loaded, used in /usr/local/lib/beagle/BeagleDaemon.exe (token 0x01000049)

** (/usr/local/lib/beagle/BeagleDaemon.exe:18396): WARNING **: The class DBus.DBusException could not be loaded, used in /usr/local/lib/beagle/BeagleDaemon.exe (token 0x01000049)

** (/usr/local/lib/beagle/BeagleDaemon.exe:18396): WARNING **: The class DBus.DBusException could not be loaded, used in /usr/local/lib/beagle/BeagleDaemon.exe (token 0x01000049)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object

```

```
ii  dbus                                  0.36.2-0ubuntu7                      simple interprocess messaging system
rc  dbus-1                                0.23.4-0ubuntu4                      simple interprocess messaging system
ii  dbus-1-utils                          0.36.2-0ubuntu7                      simple interprocess messaging system (utilit
rc  dbus-glib-1                           0.23.4-0ubuntu4                      simple interprocess messaging system (GLib-b
ii  libdbus-1-1                           0.36.2-0ubuntu7                      simple interprocess messaging system
ii  libdbus-1-cil                         0.36.2-0ubuntu7                      .NET binding for D-BUS interprocess messagin
ii  libdbus-1-dev                         0.36.2-0ubuntu7                      simple interprocess messaging system (develo
ii  libdbus-glib-1-1                      0.36.2-0ubuntu7                      simple interprocess messaging system (GLib-
```

Any ideas?

Thanks.

chap.

---

### Post by chapeaurouge on 2005-10-16
GAC output for dbus-sharp

```
`--> gacutil -l |grep dbus
dbus-sharp, Version=0.36.2.0, Culture=neutral, PublicKeyToken=9eef2692033670f5
```

---

