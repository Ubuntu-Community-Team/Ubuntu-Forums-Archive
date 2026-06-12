---
title: "How Can I Switch Back To GDM"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Ewald on 2005-12-19
I wanted to try KDE on my system and installed it using these instructions.

[https://wiki.ubuntu.com//InstallingKDE]("https://wiki.ubuntu.com//InstallingKDE")

Along with KDE, this also made KDM the default display manager.

I've decided I like GNOME better, and would like to switch back to GDM. How can I do this.

Thanks

---

### Post by tukuyomi on 2005-12-19
Hi there 

You can edit your */etc/X11/default-display-manager* and replace ```
/usr/bin/kdm
``` with ```
/usr/sbin/gdm
```

Alternatively, you can use this command: ```
sudo dpkg-reconfigure gdm
``` :)

---

