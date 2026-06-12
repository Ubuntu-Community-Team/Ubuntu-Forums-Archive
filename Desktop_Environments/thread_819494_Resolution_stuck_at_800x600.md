---
title: "Resolution stuck at 800x600"
date: 2008-06-05
forum: Desktop Environments
---

### Post by ng234 on 2008-06-05
I just installed xubuntu on a Toshiba Portege 4000 laptop. It runs great, however the screen resolution is stuck at 800x600. I would prefer a better resolution, one that actually fills up my entire monitor. Any help would be appreciated.

Thanks,
Stu

---

### Post by atomkarinca on 2008-06-05
> **ng234 said:**
> I just installed xubuntu on a Toshiba Portege 4000 laptop. It runs great, however the screen resolution is stuck at 800x600. I would prefer a better resolution, one that actually fills up my entire monitor. Any help would be appreciated.

Thanks,
Stu

If you did a fresh Xubuntu install then you might not have the "Screen and Graphics Preferences" application. Open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo apt-get install displayconfig-gtk
```

then run the application with admin privilages:

```
gksudo displayconfig-gtk
```

and configure your monitor and resolution settings. If you have nVidia card the next thing you should do is install nvidia-settings

```
sudo apt-get install nvidia-settings
```

and run it again with admin privilages:

```
gksudo nvidia-settings
```

configure your settings and hit "Save to X Configuration File". Restart the system and you should be ok.

---

### Post by whiskers751 on 2012-04-08
Check on GitHub for Toshiba-Portege-4000-Tools!

---

