---
title: "Gnome for server Ubuntu 6.06.2 LTS"
date: 2008-04-16
forum: Desktop Environments
---

### Post by marsiou on 2008-04-16
Hello,

I just installed a server LAMP, I would like to install a  light gnome .

What kind of package i need to install ?

Thanks you.

---

### Post by FakeOutdoorsman on 2008-04-16
Instead of installing a GUI on your server (and all the added bulk) you can try Webmin.  It will provide a way to edit the configuration of your server through your web browser.  If you decide Gnome is required:
```
sudo aptitude update
sudo aptitude install x-window-system-core gnome-core gnome-media gnome-system-monitor gnome-system-tools gnome-utils gnome-app-install synaptic
```

Restart your machine, log in, and then use the "startx" command to launch Gnome.

For a lighter alternative using Openbox:
```
sudo aptitude install x-window-system-core openbox obconf openbox-themes
```

startx will also launch this.

More info (including if obconf refuses to work):
[Installation / Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by marsiou on 2008-04-16
Thank you.

I will try to install this packages.

---

