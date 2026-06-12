---
title: "X11 is screwed edgy"
date: 2007-04-10
forum: Desktop Environments
---

### Post by Willagram on 2007-04-10
I tried to install Bery and Ubuntu had updates. It said a restart was required. I restarted. X cannot start anymore and I tried the reconfigure with sudo and dpkg, I tried sudo apt-get install -reinstall xserver-xorg. I even tried a backup of xorg.conf. What should I do?

---

### Post by taurus on 2007-04-10
Boot into recovery mode from GRUB menu and try to configure your X again.

```
dpkg-reconfigure xserver-xorg
```

---

