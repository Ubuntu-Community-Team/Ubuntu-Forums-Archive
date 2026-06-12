---
title: "GLib-GIO:ERROR: when running vmware player"
date: 2011-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gandip on 2011-06-20
I am not able to run vmware player in my ubuntu 11.04. The vmware player splashes and disappears hence i cannot run any vm machine. however i can see both process and memory taken by the application. when i run vmware-gksu from console i get following error.
[I][U]
vmware-gksu 
gconftool-2: /opt/rapid7/nexpose/nsc/nxpgsql/pgsql/lib/libxml2.so.2: no version information available (required by gconftool-2)
Warning: program compiled against libxml 207 using older 206
**
/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)
gconftool-2: /opt/rapid7/nexpose/nsc/nxpgsql/pgsql/lib/libxml2.so.2: no version information available (required by gconftool-2)
Warning: program compiled against libxml 207 using older 206
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Terminated[/U][/I]

I have installed Nexpose. any idea what wrong. I had same problem with vmware workstation.

---

