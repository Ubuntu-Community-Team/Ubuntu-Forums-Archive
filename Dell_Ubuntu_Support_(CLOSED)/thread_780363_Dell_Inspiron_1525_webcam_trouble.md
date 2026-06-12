---
title: "Dell Inspiron 1525 webcam trouble"
date: 2008-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sk1nnyMan on 2008-05-03
Hey

Prior to the trouble I am about to relate I had an issue where my wireless card (Intel Pro ABG 3945) was not connecting to encrypted networks with hidden SSIDs, I fixed this by installing the linux-backports-modules-2.6.24-16-generic package through Synaptic.

Since installing linux-backports-modules-2.6.24-16-generic my webcam no longer works, when I load up Ubuntu the light next to the webcam flashes once but does not work with any applications.

When I attempt to view the webcam through cheese I get the video testing picture from the Hardware testing application, if I try and view it through Ekiga I get a floating Ekiga logo but no picture.

If fixing this involves removing the linux-backports-modules-2.6.24-16-generic package then can someone point me to another fix for the wireless card issue so I can safely get rid of the backports.

Thanks

Sk1nnyman

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

