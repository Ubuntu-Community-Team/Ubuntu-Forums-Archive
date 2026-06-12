---
title: "Startup Applications entry accidentally removed"
date: 2010-07-31
forum: Desktop Environments
---

### Post by blchinezu on 2010-07-31
Sorry for bothering you with this stupid thing but I accidentally removed the low disk space notifier entry from Startup Applications.
So I would apreciate if someone could please tell me what's the command that I removed so I could put it back. Thanks.

To open Startup Applications go to** System** -> **Preferences** -> **Startup Applications** or run **gnome-session-properties** from terminal. (just in case someone wants to help but doesn't know how to)

---

### Post by ajgreeny on 2010-07-31
The only thing I can find that might relate to that is the Disk Notifications item which has the command
```
/usr/lib/gnome-disk-utility/gdu-notification-daemon
```
but I'm not sure if that is what you are looking for.

---

### Post by blchinezu on 2010-07-31
that's it:) thank you very much  for your time

---

