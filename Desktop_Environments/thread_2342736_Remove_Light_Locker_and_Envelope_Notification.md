---
title: "Remove Light Locker and Envelope Notification"
date: 2016-11-09
forum: Desktop Environments
---

### Post by slow-speed on 2016-11-09
Does anyone know how to completely uninstall Light Locker and the little envelope icon that is seen in the systray notification area in Xubuntu 14.04.5?

---

### Post by Dennis N on 2016-11-09
You can remove light-locker from the terminal with **sudo apt-get remove light-locker** or **sudo apt-get purge light-locker**. The 2nd is supposed to remove any configuration files as well as the program.

Note: you can disable it without removing the program from: Settings > Session and Startup > Application Autostart Tab > uncheck "Screen Locker"

I don't have the envelope - it may be the "mail watcher" plugin. If so, remove it from the panel with Settings > Panel > select the plugin > use the X button on the right to remove it. OR more likely if you right click on it, it may say "indicator plugin" at the top - select "properties", and for "messaging menu" check the box for "hidden". Then log out and back in and it is gone.

---

### Post by slow-speed on 2016-11-09
Thanks much, Dennis.  Got rid of light locker without any fuss.

However, your instructions for the envelope did not work.  Can't find Settings.  Did find All Setting and then Panel, but there is nothing else that fits.  Doing the right-click thing will not work for me because I don't just want it hidden, I want it uninstalled.

For the life of me, I can't figure out where it came from.  It was not there the other day when I first booted up the new OS.

---

### Post by slickymaster on 2016-11-09
Could it be the **indicator-messages** package? If yes all you have to do is ```
sudo apt-get remove indicator-messages
```

---

### Post by Dennis N on 2016-11-09
Sorry, directions I gave were not clear. For the envelope, right click on the envelope on the panel. You should see "properties".  Under "Known Indicators" you find Messaging Menu. Check the box next to it. Reboot.

---

### Post by slow-speed on 2016-11-09
slickymaster, I doubt that the item came with the indicator package.  Rather, isn't the indicator just a place where programs put their indicators?

Dennis N, yes, that was what I found.  Too bad it won't work for me.

---

### Post by slickymaster on 2016-11-10
> **slow-speed said:**
> slickymaster, I doubt that the item came with the indicator package.  Rather, isn't the indicator just a place where programs put their indicators?

Dennis N, yes, that was what I found.  Too bad it won't work for me.

The indicator applet is part of the indicator-messages package.

---

### Post by Frogs Hair on 2016-11-10
You might also check for and remove any hidden folder associated with the program.

---

