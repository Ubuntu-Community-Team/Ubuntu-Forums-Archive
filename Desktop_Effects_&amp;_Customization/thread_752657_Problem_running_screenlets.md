---
title: "Problem running screenlets"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by Genesius on 2008-04-11
Installed the latest version of screenlets from GetDeb.net, but when I run screenlets-manager I get this:

```
andy@ubuntu:~$ screenlets-manager
It looks like you are running gnome
True
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
Starter already exists.
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1675, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 323, in __init__
    self.lookup_daemon()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 369, in lookup_daemon
    self.daemon_iface = self.get_daemon_iface()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 404, in get_daemon_iface
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-zCZMLEvdZR: Connection refused

```

I'm running Hardy with E17. Hopefully screenlets work with E17, since all the Gnome files are there.

---

### Post by smartboyathome on 2008-04-12
You need to enable the dbus module in Configuration > Modules > click DBus, and click load module. Then, it should work for you.

---

### Post by Genesius on 2008-04-12
Nope. Enabled the module, same result.

---

