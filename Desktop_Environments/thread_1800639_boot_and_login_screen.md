---
title: "boot and login screen"
date: 2011-07-09
forum: Desktop Environments
---

### Post by peteyh44 on 2011-07-09
hi guys. i installed macbuntu a few months ago which changed the bootup screen and also the login screen. i have tried uninstalling macbuntu but i still have the macbuntu boot screen and login screen. i wish to reset these to the default screens but cant find out how. any help would be appreciated. cheers

---

### Post by wojox on 2011-07-09
Boot screen:

```
sudo update-alternatives --config default.plymouth
```

Login screen:

```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Logout and configure then login and run:

```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

