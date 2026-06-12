---
title: "can not open prefences dialog for AWN notification area"
date: 2012-05-13
forum: Desktop Environments
---

### Post by signalat on 2012-05-13
On ubuntu 11.10, right click doesn't work for AWN notification area applet. Can not open the preferences dialog to set the display as one row. The default two row setting makes the icon too small. Anybody can provide a %gconf.xml for the notification area applet with one row? Thanks.

---

### Post by Krytarik on 2012-05-14
Although I think you should get that preferences dialog by finding the right spot to right-click, this is the command to set that setting manually:
```
gconftool-2 --set --type int /apps/awn-applet-notification-area/icons_per_cell 1
```
To change any other of its options manually, you can use GConf-Editor.

Regards.

---

### Post by signalat on 2012-05-14
It works! Thanks.


> **Krytarik said:**
> Although I think you should get that preferences dialog by finding the right spot to right-click, this is the command to set that setting manually:
```
gconftool-2 --set --type int /apps/awn-applet-notification-area/icons_per_cell 1
```
To change any other of its options manually, you can use GConf-Editor.

Regards.

---

