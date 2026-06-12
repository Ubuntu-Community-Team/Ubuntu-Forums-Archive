---
title: "How to prevent Gnome Screensaver launching in XFCE sessions"
date: 2014-04-24
forum: Desktop Environments
---

### Post by halfbeing on 2014-04-24
Hello,

Since upgrading to 14.04 I have found that Gnome Screensaver keeps launching and making a nuisance of itself. I use XFCE and only want xscreensaver running. How can I prevent Gnome Screensaver from starting up?

---

### Post by Toz on 2014-04-24
If you upgraded from a previous version of xubuntu, then you have both light-locker and xscreensaver installed and enabled. Simply disable light-locker in Settings Manager -> Session and Startup -> Application autostart. You can kill the current process via:
```
pkill light-locker
```

---

### Post by halfbeing on 2014-04-24
Thanks for replying :)

I haven't got light-locker in my autostart and it isn't listed in my currently running processes. It must be something else.

---

### Post by Toz on 2014-04-24
Did you upgrade from an earlier version of xubuntu?

Is gnome-screensaver running?
```
ps -ef | grep "screen\|locker"
```

---

### Post by halfbeing on 2014-04-24
Yes I upgraded from Saucy. The last clean install I did was probably two releases ago, but I can't remember for certain.

gnome-screensaver isn't running right now, but only because I killed it. It will start up again before too long for no obvious reason.

---

### Post by Toz on 2014-04-24
Look for a gnome-screensaver .desktop file in /etc/xdg/autostart or ~/.config/autostart. If one is there, remove it. Also, try clearing out your saved sessions cache (in case its saved there), Settings Manager >> Session and Startup >> Session >> Clear saved sessions.

---

### Post by halfbeing on 2014-04-25
What happens in this case is that gnome-screensaver starts up again even in the middle of a session. For instance last night I checked that gnome-screensaver was not running. An hour or so later I put the machine into suspend. Just now I woke the machine from suspend and gnome-screensaver was running. I hadn't started a new session.

---

### Post by Toz on 2014-04-25
What if you uninstalled it?

---

### Post by halfbeing on 2014-04-25
It would take a couple of meta packages with it and I can imagine that leading to complications down the line, not least if I decide to start using Unity again. If I can avoid doing that it would be better.

---

