---
title: "No icons in notification area panel"
date: 2011-01-06
forum: Desktop Environments
---

### Post by danube on 2011-01-06
Hello;

haven't seen this in years since I'm using Ubuntu, but might probably be just a single step to get it back and running.

I have a notebook with Ubuntu 10.10 newly installed and since some days, there are no more icons in the notification area.

Before it stopped working, I had to do a hard shutdown because the system hung.

For now, i.e. when I go to a terminal and enter
```
nm-applet
```
I'll receive
```
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
```
Then, the Network-Manager applet appears in tray.

For me, it seems that none of the startup applications are being autostarted. There's also no kupfer started and waiting for me. No audio, no bluetooth. All the nice things running in tray when you start up.

Can someone help me here?
Thanks! Tom

---

### Post by Krytarik on 2011-01-06
Are they activated in "System -> Preferences -> Startup Applications"?

You may also check the system-wide settings:
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

---

