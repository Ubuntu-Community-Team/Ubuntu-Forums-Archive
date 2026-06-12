---
title: "Installing LXDE in normal Unity Ubuntu"
date: 2016-10-28
forum: Desktop Environments
---

### Post by dogdeblack on 2016-10-28
Hi ubuntu users.I'm currently trying to find out whats the best way to install the LXDE DE on Ubuntu with Unity DE.What I want to is to install only the minimum of LXDE so it doesn't interfere with the currently installed Unity as I also am not interested in the programs that come with it.So which package should I install?(I want it to use lightdm-locker as a lockscreen not xscreensaver)

---

### Post by CantankRus on 2016-10-28
Probably don't install the recommended packages. By default, recommended packages are considered as dependencies.
```
sudo apt install **--no-install-recommends** lxde lxde-common
```
You may have to install lxpolkit or run polkit-gnome in the lxde session to get the admin authentication window.

Have a look at the difference in packages to
```
sudo apt install lxde
```

When running both you will be given the option to continue or quit, so you can just see what's to be installed.

Make a copy of what's installed so you can easily remove if needed.

---

### Post by dogdeblack on 2016-10-28
Thanks will look into it.Also will it use light-dm as lockscreen or will I have to configure that?

---

### Post by CantankRus on 2016-10-28
You may have to add other packages for complete functionality.
You may not be even able to logout.
If so, to log out run...
```
kill -9 -1
```
I'm not really familiar with lxde.

Just look at the difference between the different install commands shown earlier 
and add what you think you may need for the session to work properly.

The different sessions are basically a window manager, a session manager a panel or dock and a set of default applications.

[COLOR="#FF0000"]Edit:[/COLOR] Just tested and for logout to work...
```
sudo apt install lxsession-logout
```

---

