---
title: "Command line to launch Democracy Player"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Luke771 on 2006-07-16
I just installed Democracy Player but GDebi Package Installer didn't add a main menu item, and I can't add one manually because I don't know the command line, I tried *democracy-player* and *democracyplayer*, neither one worked so I tried googleing but couldn't find it, so I'm asking for help here as a last resource (while I keep on googling):


What's the command line to launch Democracy Player?

---

### Post by Ramses de Norre on 2006-07-16
```
sudo updatedb && locate democracy|grep bin
```
Should reveal the executable, if there is no output you can try using another keyword than "democracy".

---

### Post by Luke771 on 2006-07-16
OK, it worked, thanks.

Anyway, the located executable was /usr/bin/democracyplayer, and /usr/bin/ is in the path, so my second guess "democracyplayer" was actually correct.

My mistake was that I didn't switch back to regular user, and when I tried to run Democracy Player as root I got the output```
root@u-box:/# democracyplayer
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 66, in ?
    onetime.OneTime()
  File "/usr/lib/python2.4/site-packages/democracy/onetime.py", line 87, in __init__
    bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 258, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1695, in dbus_bindings.bus_get
dbus_bindings.DBusException: No reply within specified time

```
Which I don't actually understand, but running 'democracyplayer' as regular user did the trick.

Anybody know what that output means?

---

### Post by lukew on 2007-04-01
> **Luke771 said:**
> OK, it worked, thanks.

Anyway, the located executable was /usr/bin/democracyplayer, and /usr/bin/ is in the path, so my second guess "democracyplayer" was actually correct.

My mistake was that I didn't switch back to regular user, and when I tried to run Democracy Player as root I got the output```
root@u-box:/# democracyplayer
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 66, in ?
    onetime.OneTime()
  File "/usr/lib/python2.4/site-packages/democracy/onetime.py", line 87, in __init__
    bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 258, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1695, in dbus_bindings.bus_get
dbus_bindings.DBusException: No reply within specified time

```
Which I don't actually understand, but running 'democracyplayer' as regular user did the trick.

Anybody know what that output means?

I am getting that error.

Looks like it might be a bug?

[HTML]https://develop.participatoryculture.org/trac/democracy/ticket/5276[/HTML]

The only other thing I can think of is that some ports need opening / forwarding but I can not find any mention of that anywhere!

Luke

---

