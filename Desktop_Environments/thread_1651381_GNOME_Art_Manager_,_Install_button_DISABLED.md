---
title: "GNOME Art Manager , Install button DISABLED"
date: 2010-12-23
forum: Desktop Environments
---

### Post by mhndm on 2010-12-23
i use the art manager program to modify the login manager, the install button is disabled , i can only download the themes .
how i can enable the install button ?

Note:
[INDENT]Ubunto netbook 10.10 with kde.
gnome-art v 0.2
[/INDENT]

---

### Post by mhndm on 2010-12-23
[IMG]http://phptransformer.com/upload/snapshot1.jpeg[/IMG]

---

### Post by mcduck on 2010-12-24
You really can't, Ubuntu uses GDM2 now, while all those themes are for the old GDM version.

GDM2 doesn't, at least yet, have support for that type of theming, but if you want you can change the background image, GTK theme, icons and fonts by launching gnome-appearance-properties as user "gdm".

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```
(You'll see two accessibility icons in the notification area after this, one will disappear once you log out and back again, the other one can be removed by going to System/Preferences/Keyboard and disabling the "Accessibility features can be toggled with keyboard shortcuts"-option).

---

