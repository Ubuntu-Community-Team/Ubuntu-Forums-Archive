---
title: "Software &amp; Updates not opening"
date: 2024-07-02
forum: Debian
---

### Post by lroy0 on 2024-07-02
hello, Software & updates does not want to open 
There is the error : 

sudo software-properties-gtk 

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 173, in activate_name_owner
    return self.get_name_owner(bus_name)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 348, in get_name_owner
    return self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 634, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'com.ubuntu.SoftwareProperties': no such name

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 210, in __init__
    proxy = bus.get_object("com.ubuntu.SoftwareProperties", "/")
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 237, in get_object
    return self.ProxyObjectClass(self, bus_name, object_path,
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 250, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 178, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 273, in start_service_by_name
    return (True, self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 634, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalid



it seems that it is a problem with python... Do you have any idea ? 
THanks in advance.
BR

---

### Post by currentshaft on 2024-07-02
What version of Ubuntu?

Also, don't run graphical applications as root.

---

### Post by lroy0 on 2024-07-02
> **currentshaft said:**
> What version of Ubuntu?

Also, don't run graphical applications as root.

debian 12

---

### Post by currentshaft on 2024-07-02
Did you mess with system Python?

Try:

sudo apt update
sudo apt install --reinstall software-properties-gtk

Any dbus errors?

sudo systemctl status dbus

---

### Post by ActionParsnip on 2024-07-02
Is Debian supported here?

---

### Post by lroy0 on 2024-07-02
> **ActionParsnip said:**
> Is Debian supported here? 
Sorry I made a mistake.

---

### Post by deadflowr on 2024-07-02
*Thread moved to **Debian***

---

