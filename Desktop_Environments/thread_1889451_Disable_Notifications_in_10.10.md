---
title: "Disable Notifications in 10.10"
date: 2011-12-01
forum: Desktop Environments
---

### Post by mafidufa on 2011-12-01
I would like to disable pop-up notifications on 10.10. A Google search lead me to use this command - ```
sudo mv   /usr/share/dbus-1/services/org.freedesktop.Notifications.service   /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
``` and restart.

Now I still get notifications, but they have changed from a pop-up to a window with a 'Close' button. 

I checked in System Monitor and Notify.osd is not running, so what is doing the notifying now, and how can I stop it, short of removing the Notification Area from the panel?

---

