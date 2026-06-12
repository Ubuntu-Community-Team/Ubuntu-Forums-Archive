---
title: "gdm theme HELP!"
date: 2010-01-06
forum: Desktop Environments
---

### Post by phoenixfire900 on 2010-01-06
how to i add this to ubuntu 9.10? [http://gnome-look.org/content/show.php/CIA+Restricted+Access?content=110149](http://gnome-look.org/content/show.php/CIA+Restricted+Access?content=110149)

---

### Post by //ro0t on 2010-01-06
> **phoenixfire900 said:**
> how to i add this to ubuntu 9.10? [http://gnome-look.org/content/show.php/CIA+Restricted+Access?content=110149](http://gnome-look.org/content/show.php/CIA+Restricted+Access?content=110149)

download ths file and install width theme installer :) it`s easey ;)

---

### Post by phoenixfire900 on 2010-01-06
what theme installer?? i tried to install this theme before but it said it was an invalid theme

---

### Post by MooPi on 2010-01-06
I beleive this theme is not compatible with 9.10. GDM has locked down the theme customization. Only thing I've been able to change is the image that represents the user login. I'm not sure if you can revert to an older gdm version.

---

### Post by phoenixfire900 on 2010-01-06
what themes are compatible and where can i find them?

---

### Post by mcduck on 2010-01-06
> **phoenixfire900 said:**
> what themes are compatible and where can i find them?

The version of GDM used in 9.10 doesn't support any specific GDM themes. So don't bother looking for any. :)

However you *can* change the background image, icons, fonts and GTK theme used in GDM. To do that open a terminal and run the following command to open the Appearance dialog as user "gdm":

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Then just select the theme & wallpaper you want  to use and close the dialog. You'll get two Assistive Technologies-icons in the notification area, the other one will disappear on it's own when you log out and back again, for the other go to System/Preferences/Keyboard and on the Accessibility-tab disable "Accessibility features can be toggled with keyboard shortcut".

---

### Post by MooPi on 2010-01-08
This thread should help .[http://ubuntuforums.org/showthread.php?t=1358026&highlight=GDM2](http://ubuntuforums.org/showthread.php?t=1358026&highlight=GDM2)

---

