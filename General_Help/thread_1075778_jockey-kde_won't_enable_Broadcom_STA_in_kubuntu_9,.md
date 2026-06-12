---
title: "jockey-kde won't enable Broadcom STA in kubuntu 9,04 alpha 4 or daily build"
date: 2009-02-20
forum: General Help
---

### Post by agim on 2009-02-20
I can't find anything on this online. I tried using jockey-kde kubuntu jaunty alpha 4.

Here is the console output:


Traceback (most recent call last):
  File "/usr/bin/jockey-kde", line 292, in on_button_toggle_clicked
    if self.set_handler_enable(h_id, 'toggle', False):
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 592, in set_handler_enable
    handler_id, enable)
  File "/usr/lib/python2.5/site-packages/jockey/backend.py", line 114, in polkit_auth_wrapper
    'org.freedesktop.PolicyKit.AuthenticationAgent', '/', False),
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PolicyKit.AuthenticationAgent was not provided by any .service files

Thanks

---

