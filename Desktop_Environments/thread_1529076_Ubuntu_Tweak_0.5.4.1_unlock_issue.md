---
title: "Ubuntu Tweak 0.5.4.1 unlock issue"
date: 2010-07-11
forum: Desktop Environments
---

### Post by prickee on 2010-07-11
When I click unlock in UT it doesn't do anything.  It was once working and now it isn't.  Here is my terminal output...


ERROR:dbus.proxies:Introspect error on :1.61:/com/ubuntu_tweak/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=0 pid=23463 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.61" (uid=0 pid=23468 comm="/usr/bin/python))

---

### Post by NikoC on 2010-07-29
I was having the same problem, but pressing ALT+F2 and running 'gksu ubuntu-tweak' solved the issue for me...

---

### Post by arturieto on 2010-09-23
Thank you Nikoc.  I followed your advice and wow my problem was solved on the unlock issue. Keep up the good things!!!

---

