---
title: "disable gdm user list not persistent"
date: 2010-03-30
forum: Desktop Environments
---

### Post by Brandon Williams on 2010-03-30
I have disabled the gdm user list using the following command:
```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```
This works until there is an update for gdm, after which the user list reappears and I have to run the command again.

I thought about adding a diversion for /var/lib/gdm/.gconf.defaults/%gconf-tree.xml so that I could edit the defaults and prevent the return of the user list, but I run Xubuntu, which already diverts that file so that it can change the default gdm configuration.

Does anyone know an alternative way to disable the user list that will be persistent without the need to redivert the gconf defaults? Or perhaps just the syntax to use for dpkg-divert that will allow me to redivert the file?

---

### Post by gzarkadas on 2010-04-04
Put the specific command (without the sudo thing) in a start-up script in /etc/init.d (copy and modify one of the existent) and place an appropriate link in all /etc/rcX.d directories for the runlevels you use before gdm loads. That way you will not miss any updates to the other gconf options that the file you mention may contain.

---

