---
title: "Ubuntu doesn't boot after upgrading to 11.10"
date: 2011-10-23
forum: Desktop Environments
---

### Post by vra5107 on 2011-10-23
HI

        For some reason ubuntu hangs on the startup screen. Tried changing the ```
/usr/sbin/lightdm to /usr/sbin/gdm inside /etc/X11/default-display-manager
```  and that doesn't work either. 

        The only way I can open the desktop is by pressing ```
Alt - F1
``` on startup screen and running ```
sudo /usr/sbin/gdm
```. Has anybody else faced this issue and if so have you been able to resolve it.

       I am running ubuntu on Dell Inspiron 1405. I am currently running Gnome 2D and hopefully like to switch to Unity as Ubuntu officially supports Unity. 

       Any help is appreciated. 

Venkat

---

### Post by araiczyk on 2011-10-24
Hey, do you still have the problem? I have the same problem and I don't know what to try.
Regards.

---

### Post by garvinrick4 on 2011-10-24
11.10 use lightdm inplace of gdm
```
sudo dpkg-reconfigure lightdm
```choose lightdm with arrows, enter and tab I believe.
Do not really need gdm anymore. Leftover on upgrade thing, not installed (gdm) on fresh install.
To restart lightdm.
sudo /etc/init.d/lightdm restart

---

