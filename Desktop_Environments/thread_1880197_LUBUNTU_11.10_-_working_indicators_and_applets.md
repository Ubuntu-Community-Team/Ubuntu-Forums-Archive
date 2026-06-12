---
title: "LUBUNTU 11.10 - working indicators and applets"
date: 2011-11-13
forum: Desktop Environments
---

### Post by rojaasensei on 2011-11-13
Just wanted to let everyone know that the following indicators/applets work in Lubuntu 11.10

 Caffeine: control screensaver from lxpanel
 Lookit: screen capture from lxpanel
 Ejecter: safely unmount USB devices from panel
 Diodon: clipboard on panel (very handy)
 Alarm Clock: from repository, not the plugin, the program, can autostart on panel with session

 The first four can be found at [http://askubuntu.com/questions/30334...ion-indicators](http://askubuntu.com/questions/30334...ion-indicators), the last in the Lubuntu Software Centre.

 Enjoy:o

---

### Post by Rodney9 on 2011-11-13
Very cool, Well done , well found. Thank You.

I'll try some of these, maybe all.

Rodney

---

### Post by rojaasensei on 2011-11-13
I'm still searching for more.

Also, wondering if anyone has tried AWN or Docky with Lubuntu 11.10.

---

### Post by croque on 2011-11-13
Mail Notification ([http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)) works well on my lubuntu 11.10 system.

Available in the repos:

```
sudo apt-get install mail-notification
```If you want the icon to display even when there is no new mail:

```
leafpad ~/.gconf/apps/mail-notification/%gconf.xml
```and add the following line after the <gconf> tag:

```
<entry name="always-display-icon" mtime="1320676101" type="bool" value="true"/>
```

---

