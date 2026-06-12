---
title: "Stalonetray: how do I add or remove apps?"
date: 2012-04-30
forum: Desktop Environments
---

### Post by cov on 2012-04-30
Hi,

I have Openbox installed with Stalonetray.

How do I add (or remove) applications from the notification area?

Currently I have the Update Manager and two instances of the Network Notification app in the notification area and I would like to remove one instance of the Network app and add stuff like the Sound Notification so that I can quickly mute when I click a link that has loud sound.

---

### Post by cov on 2012-05-06
Just a gentle bump...

---

### Post by cov on 2012-05-10
It would appear that Stalonetray uses the **/etc/xdg/autostart/** directory to configure the system tray.

In the case of the sound applet it was **gnome-sound-applet.desktop** which had the line:

OnlyShowIn=GNOME;Unity;

After I commented this line out, it appeared in the notification area.

---

