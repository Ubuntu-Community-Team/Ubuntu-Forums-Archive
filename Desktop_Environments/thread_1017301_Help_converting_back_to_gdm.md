---
title: "Help converting back to gdm"
date: 2008-12-20
forum: Desktop Environments
---

### Post by PhoenixTKO on 2008-12-20
OK so I originally started out with Ubuntu and than I switched my display manager over to KDE. Well now I dont want to use it no more and now its telling me I cant get into my login window options in the system/admin/ section because I need to be running GDM.

The problem I'm having is that I cant get GDM to run. I tried logging out and changing the session to gdm and I even changed the default-display-manager file in etc/X11/ so that it now reads "/usr/bin/gdm" but when I restart I still get the Kubuntu load up screen instead of Ubuntu.

How do I convert back to GDM?? 
Any ideas?
Thanks.

---

### Post by albinootje on 2008-12-20
> **PhoenixTKO said:**
> 
The problem I'm having is that I cant get GDM to run. I tried logging out and changing the session to gdm and I even changed the default-display-manager file in etc/X11/ so that it now reads "/usr/bin/gdm" but when I restart I still get the Kubuntu load up screen instead of Ubuntu.


What about :
```

sudo apt-get remove --purge kdm
sudo /etc/init.d/gdm restart

```

---

### Post by kellemes on 2008-12-21
```
sudo dpkg-reconfigure gdm
```

---

