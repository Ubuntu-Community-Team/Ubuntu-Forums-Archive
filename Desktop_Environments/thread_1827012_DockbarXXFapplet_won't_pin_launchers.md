---
title: "DockbarX/XFapplet won't pin launchers"
date: 2011-08-17
forum: Desktop Environments
---

### Post by Pirate Zoro on 2011-08-17
I decided to try DockbarX in XFCE to see how it worked compared to Talika. It runs a bit smoother, and looks a lot better, the only problem is, I can't pin any open programs to my dock. If I click "pin application" and then close the window, the icon disappears as if I never pinned it. This has happened with every program I've tried. I've also tried running it as a stand-alone dock, and while I can pin programs that way, the dock itself likes to move around on its own. I am using the version from the WebUpd8 repos, which is version 0.46. Can someone tell me what's going wrong? Or does it not work well with XFCE?

EDIT: Not only does the pin option not work, non of the right-click menu options, including the quicklists, work. I can minimize/restore by clicking the icon, but I can't use the menus.

---

### Post by M7S on 2011-08-17
Post your .dockbarx/log/dockbarx.log

---

### Post by Pirate Zoro on 2011-08-17
There are six logs in said folder, numbered from .1-.6, which exactly am I looking for?

---

### Post by M7S on 2011-08-18
dockbarx.log contains info from the last run, dockbarx.log.1 from the time before that and so on. If you experienced this run the last time you used dockbarx, send dockbarx.log, otherwise send .1 or .2 or whenever it happened.

---

### Post by Pirate Zoro on 2011-08-18
OH, okay. Here's the most recent log:
```
INFO	| 2011-08-17 14:47:59,637	| DockbarX 0.46
INFO	| 2011-08-17 14:47:59,638	| DockbarX init
INFO	| 2011-08-17 14:48:00,457	| DockbarX reload
ERROR	| 2011-08-17 14:48:00,908	| /usr/lib/pymodules/python2.7/dockbarx/common.py:850: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.colors[c] = GCONF_CLIENT.get_value(color_dir + "/" + c)
ERROR	| 2011-08-17 14:48:00,939	| Restarting DockManager Helpers failed.
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dockbarx/dockmanager.py", line 142, in reset
    "/net/launchpad/DockManager/Daemon")
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name net.launchpad.DockManager.Daemon was not provided by any .service files
ERROR	| 2011-08-17 14:48:02,545	| /usr/bin/dockbarx_factory:70: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  "dockbar applet", "0", dockbar_factory)
```

---

### Post by Pirate Zoro on 2011-08-19
What exactly am I looking for in the log? I see there are a number of errors, what am I trying to fix?

---

### Post by M7S on 2011-08-19
Sorry, non of these errors are anything out of the ordinary. Nothing to do there. The problem is probably in XFapplet so I can't help you, except saying that some time in the future I hope DockbarX will run natively in xfce. One guy promised to start working on it but I haven't heard from him since. If I only found some good documentation over Xfce-panelplugins for python I'd do it myself.

---

### Post by Pirate Zoro on 2011-08-19
I was afraid that might be the case. Thank you anyway for offering to help :) I'm using Talika right now, but I'll definitely keep my eye out for new releases and keep trying. Once again, thank you :)

---

