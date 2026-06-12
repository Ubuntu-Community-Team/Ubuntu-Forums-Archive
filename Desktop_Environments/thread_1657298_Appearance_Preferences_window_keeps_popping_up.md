---
title: "Appearance Preferences window keeps popping up"
date: 2011-01-01
forum: Desktop Environments
---

### Post by inkameep on 2011-01-01
After I changed my "Theme," the "Appearance Preferences" window started opening automatically every time I boot ubuntu, before I even get to the login screen. How do I fix this?

---

### Post by Krytarik on 2011-01-01
Check if there is "gnome-appearance-properties.desktop" in the directory "/usr/share/gdm/autostart/LoginWindow".
```
ls /usr/share/gdm/autostart/LoginWindow
```
If so, delete it.
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Greetings

---

### Post by inkameep on 2011-01-02
Thanks. I followed your instructions and it worked.

---

