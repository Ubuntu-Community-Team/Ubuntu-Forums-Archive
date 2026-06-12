---
title: "How do i change default display manger?"
date: 2008-11-04
forum: Desktop Environments
---

### Post by MasterNetra on 2008-11-04
Originally i installed Ubuntu 8.10 so i have gnome. More recently i decided to take a look at Kubuntu's desktop so i installed that, keeping gdm as default. Now I've fallen in love with kde4.1 and trying to make kde default. How do I do this?

---

### Post by overdrank on 2008-11-04
> **MasterNetra said:**
> Originally i installed Ubuntu 8.10 so i have gnome. More recently i decided to take a look at Kubuntu's desktop so i installed that, keeping gdm as default. Now I've fallen in love with kde4.1 and trying to make kde default. How do I do this?

Hi and at the login screen when you select sessions, select KDE and then it will ask to set as default.

---

### Post by MasterNetra on 2008-11-04
My bad not the actual desktop but enviroment in general. The Login screen is still gnome. I'm trying to visually convert the entire system to Kubuntu's style.

---

### Post by benerivo on 2008-11-04
You need to edit```
/etc/X11/default-display-manager
```from memory, you just need to put the one you want at the top of the list.

---

### Post by MasterNetra on 2008-11-04
> **benerivo said:**
> You need to edit```
/etc/X11/default-display-manager
```from memory, you just need to put the one you want at the top of the list.

Where is the kde thing? Its not in the /usr/sbin with gdm.

---

### Post by benerivo on 2008-11-04
Is kdm definitely installed? Try```
whereis kdm
```in a console. Another way to change the display manager is to install another one such as xdm. Then you get to choose again, and once you've chosen kdm, then you can uninstall xdm.

---

### Post by MasterNetra on 2008-11-04
> **benerivo said:**
> Is kdm definitely installed? Try```
whereis kdm
```in a console. Another way to change the display manager is to install another one such as xdm. Then you get to choose again, and once you've chosen kdm, then you can uninstall xdm.

Thanks I'll do that for now on! :)

---

