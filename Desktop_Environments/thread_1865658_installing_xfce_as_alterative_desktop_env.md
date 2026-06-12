---
title: "installing xfce as alterative desktop env"
date: 2011-10-20
forum: Desktop Environments
---

### Post by moody_mark on 2011-10-20
Hi folks. I have a Ubuntu 10.10 machine and I wanted to try installing the xubuntu desktop so i could choose the normal gnome environment or the xcfe, however it started showing a xubuntu splash screen on boot and also the login page. While this isnt a massive issue, i just wanted to keep the machine the same, with all the usual splash screens and login window, with the usual "Ubuntu" theme login, but just choose xfce at login time.

I installed the "xubuntu-desktop" package and this is what changed the splash screen and login screen. How do i revert?

---

### Post by 3Miro on 2011-10-20
xubuntu-desktop changes the splash screen. xfce4 installs just he minimum of xfce.

You can try installing Ubuntu-desktop, which should change the settings back to default Ubuntu. This will probably uninstall xubuntu-desktop, but this will NOT uninstall xfce4. Just keep an eye for packages like xfce4-panel, xfwm4 and xfdesktop, so long as those are not removed, you will keep xfce4.

---

### Post by Harry.k on 2011-10-20
yup. Reinstall ubuntu-desktop. That should fix it

---

### Post by moody_mark on 2011-10-20
Thanks, but i re-installed ubuntu-desktop from synaptic and its still got the xubuntu splash screen and login. I did prior to that uninstall xubuntu-desktop which surprises me that the splash screen has remained etc.

---

### Post by 3Miro on 2011-10-20
xubuntu-desktop doesn't do anything by itself, it simply install a whole bunch of other components that make up xfce and the xfce splash screen. If you remove xubuntu-desktop, then this will not revert any of the change, you will have to change things back one at a time.

Ubuntu-desktop should have reverted the splash screen back to the default, but I guess it didn't. You can do this manually, here are couple of HowTos that I found:

[http://www.rockytophome.com/index.php?option=com_content&view=article&id=94:howto-change-plymouth-theme-in-ubuntu-1010&catid=36:linux-related&Itemid=55](http://www.rockytophome.com/index.php?option=com_content&view=article&id=94:howto-change-plymouth-theme-in-ubuntu-1010&catid=36:linux-related&Itemid=55)

[http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04](http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04)

[http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html](http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html)

I guess you can try the commands:
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

---

### Post by moody_mark on 2011-10-20
Thanks, the plymouth thing sorted the splash screen but not the login screen. In the end I used synaptic to deselect anything "xubuntu" related.

---

