---
title: "Desktop locked after upgrade to 14.04"
date: 2014-04-20
forum: Desktop Environments
---

### Post by bkline on 2014-04-20
I upgraded one of my workstations to Trusty and now all of a sudden after a certain amount of inactivity the desktop locks, even though I have the screensaver settings set to never do that. Has the latest version of Xfce added a second place I need to configure that?

---

### Post by Toz on 2014-04-21
In an upgrade scenario, light-locker is added and enabled as the new locking mechanism but xscreensaver is not disabled and/or removed. You probably have both running (there are two screensaver entries in Settings Manager). You should kill the process of one of them and uncheck the corresponding entry in Settings Manager -> Session and Startup -> Application startup so it doesn't autostart.

Optionally, you can uninstall one of them.

As a heads up, there is currently an [active bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736") with light-locker that may affect you where the screen goes blank after unlock.

---

### Post by bkline on 2014-04-21
Thanks, Toz. I'll uninstall one of them. It would be nice if they didn't introduce these little surprises without prominent notification.

---

### Post by ccrs8 on 2014-04-21
I'm having a similar problem except that I did a clean install of Xubuntu 14.04.  Attached are both my Light Locker Settings and my Display settings.  These are the only two settings sections that I can find regarding any sort of session locking.  But my screen is getting locked after 15 minutes of inactivity, even if that inactivity is watching a movie (which xscreensaver in versions 13.10 and older never considered inactivity).  So I guess the questions are:

1) Where can I find the setting that is making my screen lock after 15 minutes?
2) Is it possible to disable this when a movie is playing?

Light Locker:
[ATTACH=CONFIG]252355[/ATTACH]

Display:
[ATTACH=CONFIG]252356[/ATTACH]

---

### Post by bkline on 2014-04-22
You might try uninstalling light locker, the newly introduced variable. It's know to have bugs.

---

### Post by ccrs8 on 2014-04-22
> **bkline said:**
> You might try uninstalling light locker, the newly introduced variable. It's know to have bugs.

My 14.04 is a new install - I no longer have xscreensaver on my machine.

---

### Post by bkline on 2014-04-22
Try this:
```
sudo apt-get install xscreensaver
```

---

