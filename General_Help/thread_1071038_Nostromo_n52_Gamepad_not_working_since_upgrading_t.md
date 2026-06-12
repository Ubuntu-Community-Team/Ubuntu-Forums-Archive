---
title: "Nostromo n52 Gamepad not working since upgrading to Ibex"
date: 2009-02-15
forum: General Help
---

### Post by B0rat on 2009-02-15
My [_n52 gamepad_](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=164714) was working perfectly using the required software from Sourceforge. Now when starting [_the software_](http://sourceforge.net/projects/nostromodriver) from a terminal I see this:

Feb 15 23:20:16 jupiter nostromo_daemon[14010]: Removing stale pidfile.
Feb 15 23:20:16 jupiter nostromo_daemon[14010]: Nostromo device not found.
Feb 15 23:20:16 jupiter nostromo_daemon[14010]: Couldn't find any supported devices.
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: Removing stale pidfile.
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: Found 050d:0815 at dev 2
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: **Failed to grab: Device or resource busy**
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: Starting reader_thread with fd=9 
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: Found 050d:0815 at dev 3
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: **Failed to grab: Device or resource busy**
Feb 15 23:20:36 jupiter nostromo_daemon[14051]: Starting reader_thread with fd=10

It's like something new in the distro or kernel is preventing the software from seeing the device.

What would have changed that is causing this?

---

