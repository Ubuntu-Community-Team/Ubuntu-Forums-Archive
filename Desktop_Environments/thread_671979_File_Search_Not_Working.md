---
title: "File Search Not Working"
date: 2008-01-19
forum: Desktop Environments
---

### Post by chazchaz101 on 2008-01-19
The built in desktop search feature is not working for me at all. When I search for a file, even by its exact name and with the location set to its parent folder, i get nothing.

So far, I have tried: multiple restarts, updated (sudo updated) and restarting trackerd. When I try to restart trackerd after killing it, as a user, I get the following error:
```


user@Laptop:~$ trackerd


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0

```
after which I just get a flashing cursor.

When I try to start trackerd as sudo instead, I get
```

user@Laptop:~$ sudo trackerd


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Throttle level is 0
ERROR: tracker_dbus_init() could not get the session bus
DBUS ERROR: org.freedesktop.DBus.Error.NoReply occurred with message Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
process 6405: arguments to dbus_connection_register_object_path() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5280.
This is normally a bug in some application using the D-Bus library.


```
with the same blinking cursor.

Neither of these things has made any difference.

Any ideas?

---

### Post by Thund3rstruck on 2008-01-19
Not sure about the built-in search tools since I always use the CLI. 

```

find [path] [options] [arguments]

If you need to search outside your home directory then prefix find with sudo.

$ find / -name firefox

Find Manual
$ man find

```

---

### Post by chazchaz101 on 2008-01-21
Thanks for the help. I don't mind using the command line, but it seems odd that the GUI search doesn't seem to work.

---

### Post by luctor on 2008-01-22
i've ditched trackerd and installed beagle
works way better for me

---

### Post by dbera on 2008-01-22
There are some dbus related error in your desktop session. If you do from a terminal "ps aux | grep dbus" you should see several lines with "dbus" in it. Tracker relies on this dbus to communicate within its components.

If you need tracker in future, I would suggest searching for the dbus error or asking about the dbus error in the irc/forum/mailing-list. That will get you a quicker answer.

---

