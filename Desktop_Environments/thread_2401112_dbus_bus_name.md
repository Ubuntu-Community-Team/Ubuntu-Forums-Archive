---
title: "dbus bus name"
date: 2018-09-13
forum: Desktop Environments
---

### Post by luca31 on 2018-09-13
Hi all, if an application uses dbus for signaling o ipc, is there a way to get its bus name in order to be able to do introspection/monitoring on its objects with gdbus?
In other words where/how I can find the well known bus name of an app? Is there a way to catch it on the bus?

thanks

Luca

---

### Post by luca31 on 2018-09-13
I managed to get the list of bus name using the /org/freedesktop/DBus object that reside in the org.freedesktop.DBus bus name (rappresenting the bus itself)
$ gdbus call --system --dest org.freedesktop.DBus --object-path /org/freedesktop/DBus --method org.freedesktop.DBus.ListNames
$ gdbus call --session --dest org.freedesktop.DBus --object-path /org/freedesktop/DBus --method org.freedesktop.DBus.ListNames

regards

Luca

---

