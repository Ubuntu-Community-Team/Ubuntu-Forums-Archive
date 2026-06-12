---
title: "KDE for VNC"
date: 2006-08-02
forum: Desktop Environments
---

### Post by koolguynet on 2006-08-02
I have a working VNC setup that I like, but just want to know how to change from Gnome to KDE.  Any ideas?  I think I need to edit /etc/X11/Xsession

---

### Post by aysiu on 2006-08-02
Log out and select a KDE in the **session** menu of the login screen?

---

### Post by koolguynet on 2006-08-02
How I have VNC setup, it just goes straight past the login screen.  I initiate vncserver as a user and then login to that port.  In other words, I never see a login screen.

---

### Post by aysiu on 2006-08-02
Try this: ```
sudo aptitude update
sudo aptitude install xnest
gdmflexiserver --xnest
``` Then select KDE...?

---

