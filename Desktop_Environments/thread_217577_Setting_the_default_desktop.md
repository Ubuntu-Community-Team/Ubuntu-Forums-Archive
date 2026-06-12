---
title: "Setting the default desktop"
date: 2006-07-17
forum: Desktop Environments
---

### Post by mdelorme on 2006-07-17
Hello,

I recently installed ubuntu-desktop on my kubuntu installation.  Unfortunately, this has changed the default desktop to Gnome for all users.  I know that I can change this at the login screen on a per-user basis (and have already done so for my login), however I would like to know how I can change the default desktop back to KDE globally (without removing gnome).  This also presents a problem because Gnome is now launched as my default desktop whenever I run vncserver, and I am having some trouble getting KDE to launch instead.

---

### Post by aysiu on 2006-07-17
Have you tried switching the default display manager from /usr/sbin/gdm to /usr/bin/kdm in /etc/X11/default-display-manager?

If not, some config file in /etc/X11 may have the default desktop environment. I would assume, though, that KDM would default to KDE.

---

### Post by lvleph on 2006-07-17
I ended up giving up on this and just uninstalled gdm. That of course fixed it for me.

---

### Post by Ramses de Norre on 2006-07-17
In case you ever want to try again I think this would have fixed it: ```
sudo ln -s /etc/init.d/kdm /etc/rc2.d/S13kdm
echo "/usr/bin/kdm"|sudo tee /etc/X11/default-display-manager
```

---

### Post by mdelorme on 2006-07-17
Yeah, following that exact train of thought I made sure that when I installed ubuntu-desktop I chose kdm as my desktop manager. Unfortunately my system's default desktop was still changed to Gnome.

---

### Post by amr2205 on 2006-07-30
> **Ramses de Norre said:**
> In case you ever want to try again I think this would have fixed it: ```
sudo ln -s /etc/init.d/kdm /etc/rc2.d/S13kdm
echo "/usr/bin/kdm"|sudo tee /etc/X11/default-display-manager
```

Thank you! I've been searching a solution for this. :D

---

