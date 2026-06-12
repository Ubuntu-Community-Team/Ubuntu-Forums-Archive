---
title: "Change background gnome-"
date: 2019-03-06
forum: Desktop Environments
---

### Post by zevues on 2019-03-06
Hi guys,
I'm using Xubuntu 18.04 and I changed the default with:
```

apt purge light-locker
apt install gnome-screensaver

```

The problem is that I can't change the default wallpaper of the lock screen.

I tried:
**1-way**
```

gsettings set org.gnome.desktop.screensaver picture-uri file://image.jpg
gconftool update

```
but nothing changed even if the command:
```
gsettings get org.gnome.desktop.screensaver picture-uri
```
gives the right value.

**2-way**
I tried to follow [this]("https://help.gnome.org/admin/system-admin-guide/stable/desktop-shield.html.en") tutorial and so:
```

apt install dconf-cli
edited the file: /etc/dconf/profile/gdm
mkdir /etc/dconf/db/gdm.d/
created the file: /etc/dconf/db/gdm.d/01-screensaver
dconf update
reboot the system

```
but nothing changed.

**3-way**
As a last resort I tried to link my image as:
```

ln -s image.jpg /usr/share/xfce4/backdrops/xubuntu-wallpaper.png

```
because this is the wallpaper that gnome-screensaver uses as default.

Any suggestion?

---

