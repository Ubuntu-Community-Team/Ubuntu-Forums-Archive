---
title: "Frustration with Dual Monitor Settings..."
date: 2010-05-11
forum: Desktop Environments
---

### Post by jfbilodeau on 2010-05-11
Greetings,

I spend an hours fighting with the new KDE multiple monitor setup. For some reason, it would not allow me to select the highest (auto) resolution on my laptop and an exernal monitor. Everytimes I applied the configuration (1280x800, 1440x900), both screens would reset to 1024x768.

After playing with xrandr, it turned out that the xorg.conf file was limited to 2560x2560. Thus, I could not apply my desired resolution of 2720x900.

My two frustration is that the KDE System Settings quietly ignored the problem, and reset my setup for me. The second is the limited default desktop size.

After increasing my virtual screen size in xorg.conf, the problem is fixed.

Ok, so I admit that this is a rant and not a request for support. I'm off to visit Bugzilla now...

J-F

---

