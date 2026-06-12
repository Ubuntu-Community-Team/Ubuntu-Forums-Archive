---
title: "gnome-screensaver"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Zmija on 2006-08-14
Yellow... ;) 

How can I Disable gnome-screensaver at all... I mean to revome service "gnome-screensaver" in System Monitor...

[IMG]http://www.slibe.com/slibe/b04ecaea-gnome-screensave.png[/IMG]


THNX to all in advance...

---

### Post by 23meg on 2006-08-14
```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
```and restart GNOME.

---

### Post by Zmija on 2006-08-14
and after that screensaver won't start on next reboot?


THNX man ;)

---

### Post by 23meg on 2006-08-14
It shouldn't. If it does, try ```
sudo chmod -x /usr/bin/gnome-screensaver
```

---

### Post by Zmija on 2006-08-14
```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
```

This is working... :)

LOCK ;)

---

### Post by 23meg on 2006-08-14
Good to know. I don't know why you're disabling gnome-screensaver but in case you need them, I wrote two guides related to it:

[http://www.ubuntuforums.org/showthread.php?t=198809](http://www.ubuntuforums.org/showthread.php?t=198809)
[http://www.ubuntuforums.org/showthread.php?t=195557](http://www.ubuntuforums.org/showthread.php?t=195557)

---

