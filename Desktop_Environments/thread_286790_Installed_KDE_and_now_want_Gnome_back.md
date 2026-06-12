---
title: "Installed KDE and now want Gnome back"
date: 2006-10-28
forum: Desktop Environments
---

### Post by mattgaunt on 2006-10-28
Hey every, i was using Gnome and then install XGL/Compiz (or beryl should i say) anyway it had a few problems that a few people said Kubuntu could fix so i installed the Kubuntu desktop, and it asked if i wanted KDE to be my defualt window manager instead of GDM and i said yes, now ive been trying desperately to get Gnome back cos i did prefer it but when i log into a session im not asked if i want Gnome to be default

Does any1 kno who i can get GDM back to default

Thanks alot

---

### Post by aysiu on 2006-10-28
```
sudo nano -B /etc/X11/default-display-manager
``` Change /usr/bin/kdm to /usr/sbin/gdm

---

