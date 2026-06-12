---
title: "Nautilus display folder as file icon as well"
date: 2018-03-02
forum: Desktop Environments
---

### Post by jtodd.fr on 2018-03-02
When launching with nautilus by command `nautilus --no-desktop` (for I have desktop display issue previously), all folders are displayed like file icon, shown as [https://imgur.com/a/tv6uA](https://imgur.com/a/tv6uA)

Console prints warning below

```

** (nautilus:19889): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-ZXGWTRRupv: Connection refused


(nautilus:19889): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
sys:1: PyGIWarning: Nautilus was imported without specifying a version first. Use gi.require_version('Nautilus', '3.0') before import to ensure that the right version gets loaded.
/usr/share/nautilus-python/extensions/nautilus-admin.py:18: PyGIWarning: GConf was imported without specifying a version first. Use gi.require_version('GConf', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import Nautilus, GObject, GConf, Gtk, GLib

```

Adding foolowing lines to /usr/share/nautilus-python/extensions/nautilus-admin.py get rids of the last warning 

```

import gi


gi.require_version('GConf', '2.0')



```

But others remains and not sure if that's related or not. What's missing that leads to nautilus displays folder as file icon? And possible fix? 

Thanks

---

