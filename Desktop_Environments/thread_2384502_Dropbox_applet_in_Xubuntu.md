---
title: "Dropbox applet in Xubuntu"
date: 2018-02-08
forum: Desktop Environments
---

### Post by awachens on 2018-02-08
Hi! Good morning. I have Xubuntu installed and need some help. When i install Dropbox in panel add an icon with forbidden symbol... How i can resolve this ?

Regards !

---

### Post by speartip on 2018-02-08
Age old problem that's still not been fixed.
The only workaround that I've found is to add a new start up item in - session & startup - application autoatart - with the following code in the command line:
```
[SIZE=3]/bin/bash -c "sleep 15 && dropbox stop && env DBUS_SESSION_BUS_ADDRESS="" dropbox start -i"[/SIZE]  
```
This stops the original Dropbox instance from the notification area in the panel & starts it again normally, where you now have access to the right click menu.

---

