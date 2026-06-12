---
title: "Internet and USb nto recognized"
date: 2008-12-03
forum: Desktop Environments
---

### Post by StickFigure37 on 2008-12-03
I installed KDE via apt-get yesterday  and since then I can't connect to the internet or access any of my usb devices when in KDE. Everything still works fine in Gnome so I'm guessing it's  problem with my KDE install. Solutions?

---

### Post by sayakb on 2008-12-04
Plug in the USB device and post the output of **lsusb**.

For the internet issue, right click on KNetworkManager and see if you haven't set up a manual configuration for eth0

---

