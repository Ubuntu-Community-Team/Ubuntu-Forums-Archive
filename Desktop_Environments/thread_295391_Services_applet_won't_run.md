---
title: "Services applet won't run"
date: 2006-11-08
forum: Desktop Environments
---

### Post by flabbah on 2006-11-08
In XFCE, I selected Applications -> System -> Services, and then unchecked the service for the HP printer support. The applet died, and despite rebooting, will no longer run.

When I run the GUI, it just says :

The configuration could not be loaded
You are not allowed to access the system configuration.

So then I try sudo services-admin, and get this:

(services-admin:4441): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4441: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4441: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4441): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4441: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

Anybody have any ideas ? Thanks.****

---

