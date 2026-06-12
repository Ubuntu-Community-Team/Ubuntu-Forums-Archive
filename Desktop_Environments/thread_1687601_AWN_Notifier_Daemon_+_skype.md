---
title: "AWN Notifier Daemon + skype"
date: 2011-02-14
forum: Desktop Environments
---

### Post by quattroman on 2011-02-14
Does anybody got the AWN applet "Notifier Daemon" to work with skype task/notifier icon? 

I removed every single applet from the gnome bar before turning it off with Ubuntu Tweak. Still when I click close on Skype it doesn't go to the notifier/taskbar, but it is still running in the background.

Please help, and if there is a better alternative applet for the notifier daemon, it would be great.

Thanks

---

### Post by quattroman on 2011-02-14
Found solution. It is called Notification Area: A notification Area (systray). I think it was downloaded from the following command line.

```
sudo apt-get install avant-window-navigator-trunk python-awn-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-extras-trunk

```

Not all pretty but functional.

---

### Post by Copper Bezel on 2011-02-14
Add an Indicator Area, too. Some apps show up in Notifier if Indicator isn't present, some don't.

The pretty is adjustable - just right-click the applet.

---

### Post by quattroman on 2011-02-15
thanks

---

