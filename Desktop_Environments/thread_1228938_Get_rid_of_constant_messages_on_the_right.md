---
title: "Get rid of constant messages on the right"
date: 2009-08-01
forum: Desktop Environments
---

### Post by kernel89 on 2009-08-01
I keep getting these messages from Pidgin and, for ubuntu updates, and so on.
How do I get rid of it?

[http://i25.tinypic.com/245bqjb.png](http://i25.tinypic.com/245bqjb.png)

---

### Post by nperry on 2009-08-01
> **kernel89 said:**
> I keep getting these messages from Pidgin and, for ubuntu updates, and so on.
How do I get rid of it?

[http://i25.tinypic.com/245bqjb.png](http://i25.tinypic.com/245bqjb.png)

```
neil@desktop:~$ ps aux | grep notify
neil      3546  0.0  0.2 175100 16664 ?        S    15:42   0:04 /usr/lib/notify-osd/notify-osd

```

This should be able to be removed from Services iirc.

I've just done a google search and came up with this to remove it fully.

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

---

### Post by kernel89 on 2009-08-01
> **nperry said:**
> ```
neil@desktop:~$ ps aux | grep notify
neil      3546  0.0  0.2 175100 16664 ?        S    15:42   0:04 /usr/lib/notify-osd/notify-osd

```

This should be able to be removed from Services iirc.

I've just done a google search and came up with this to remove it fully.

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```


I just tried it, 
this one

"sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled"

dit not work, I keep getting the messages.

---

### Post by russo.mic on 2009-08-02
just worked for me...did you log out and log back in?

---

