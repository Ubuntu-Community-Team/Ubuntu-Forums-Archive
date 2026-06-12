---
title: "Xubuntu 14.10 password required after boot to console and startx"
date: 2014-10-14
forum: Desktop Environments
---

### Post by maier.m on 2014-10-14
Hi,

I am running Xubuntu 14.10 and have configured the system to boot into console and bring up the Xubuntu desktop manually using startx. So here's what I did:

changed /etc/default/grub to have
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="text"
```

and /etc/environment to set the variables to the Xubuntu session 
```
# make Xubuntu session the default
XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/usr/share/upstart/xdg:/etc/xdg:/etc/xdg
XDG_SESSION_DESKTOP=xubuntu
XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share
```

The strange thing now, if I startx, graphical desktop comes up with a black screen and asks for my password. This is not an additional login window asking for username/password, just an authentication window asking for the password I cannot even find out what for. If I enter the password, the Xubuntu sessions comes up right away. If I don't enter anything, dialog window goes away after about 25 seconds and Xubuntu session also comes up.

Does anyone have an idea how to find out what this password dialog is for and how to get rid of it?

Thanks
Markus

---

### Post by maier.m on 2014-10-29
really no one an idea?

---

