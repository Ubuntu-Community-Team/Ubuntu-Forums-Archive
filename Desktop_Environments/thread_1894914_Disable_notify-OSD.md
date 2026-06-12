---
title: "Disable notify-OSD"
date: 2011-12-13
forum: Desktop Environments
---

### Post by thomsmells on 2011-12-13
Is there a way for me to remove the bubble notifications? I don't want to replace it with another notification system, I just want to disable them altogether.

---

### Post by Megaptera on 2011-12-13
Until someone else comes along, I used this to alter various aspects of OSD in 10.04 is this any help? I cut the default time, location, size and shape.

[http://ubuntuexplore.blogspot.com/2010/06/ubuntu-customized-notification-osd.html](http://ubuntuexplore.blogspot.com/2010/06/ubuntu-customized-notification-osd.html)

---

### Post by wojox on 2011-12-13
Same way we have always done it:
```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 
```

Restart. :P

---

### Post by thomsmells on 2011-12-14
mv: cannot stat `/usr/share/dbus-1/services/org.freedesktop.Notifications.service': No such file or directory

Does this not work for 11.10? Or do I need to install something first?

---

