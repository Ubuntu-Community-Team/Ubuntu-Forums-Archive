---
title: "[SOLVED] Switch Desktop Managers"
date: 2008-12-19
forum: General Help
---

### Post by moonscapex on 2008-12-19
I recently installed KDE.  When it was installing a dialog came up asking what desktop manager to use (KDM or GDM).  How do I switch between the two?

---

### Post by jimmy the saint on 2008-12-19
These only affect the login screen.  it really doesn't matter which one you use.  In either one, you can choose which session to use, which will dictate whether you log into gnome (ubuntu) or KDE (Kubuntu).

---

### Post by bodhi.zazen on 2008-12-19
> **moonscapex said:**
> I recently installed KDE.  When it was installing a dialog came up asking what desktop manager to use (KDM or GDM).  How do I switch between the two?

Open a terminal and enter :

```
sudo dpkg-reconfigure gdm
```

This will call up a text dialog and you can select KDM or GDM (use the arrow keys and enter key).

These applications are the log in screen (well a little more then that) and from either you can select a "session" which allows you to choose to start either Gnome or KDE.

HTH

---

