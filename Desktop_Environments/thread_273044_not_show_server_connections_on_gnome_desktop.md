---
title: "not show server connections on gnome desktop"
date: 2006-10-07
forum: Desktop Environments
---

### Post by harty83 on 2006-10-07
Is there a way to configure gnome so that it will not show server connections on the desktop but only under Places or in network:///?  

Alan

---

### Post by CatKiller on 2006-10-07
```
gconf-editor
``` and then apps/nautilus/desktop uncheck "network_icon_visible".

---

### Post by harty83 on 2006-10-07
Thanks for the reply.  

I don't mean the actual "Network Servers" icon.  I meant the icons that show up when I create a server connection such as a ftp or ssh connection.  For example, I made a ftp connection to my webhost HostMonster.  Gnome adds an icon to the desktop called "HostMonster."  I don't want that.  I have multiple server connections that I don't want to have to set up everytime but nor do I want to clutter up my desktop with all the icons!

Thanks!
Alan

---

### Post by harty83 on 2006-10-07
never mind. same steps but just uncheck "volumes_visible."

Thanks
Alan

---

### Post by CatKiller on 2006-10-07
Glad you got it sorted anyway.

---

