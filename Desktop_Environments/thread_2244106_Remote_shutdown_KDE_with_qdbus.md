---
title: "Remote shutdown KDE with qdbus"
date: 2014-09-13
forum: Desktop Environments
---

### Post by sgofferj on 2014-09-13
Hi,

under Opensuse I had a script to shutdown my desktop machine remotely by ssh'ing to the machine and executing my script:

```

#/bin/bash
export DISPLAY=:0
qdbus org.kde.ksmserver /KSMServer logout 0 2 2
```

However, under kubuntu, I get

```
 Could not connect to D-Bus server: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-yjs7O10zzS: Connection refused
```

Any ideas on that?

-S

---

### Post by gordintoronto on 2014-09-14
Try this command: sudo shutdown -h now

(It might not need sudo.)

---

### Post by sgofferj on 2014-09-14
Shutdown does NOT properly end GUI applications - it just HUPs or TERMs them - and the KDE session also will not be saved. There is a reason why I want to send a logout-shutdown message to KSMServer...

---

### Post by sgofferj on 2014-09-14
Got the solution from the KDE forums:

New script:
```

#/bin/bash
ADDRESS="$(tr '\0' '\n' < /proc/$(ps -Ao %p%c | sed '/ksmserver/!d; s/ *\([0-9]*\) *.*/\1/g')/environ | grep DBUS_SESSION_BUS_ADDRESS |  cut -d"=" -f2-)"
qdbus --address "$ADDRESS" org.kde.ksmserver /KSMServer logout 0 2 2
```

---

