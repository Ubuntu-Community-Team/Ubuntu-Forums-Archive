---
title: "How to switch Kubuntu back to Ubuntu? [Resolved]"
date: 2007-06-02
forum: Desktop Environments
---

### Post by Linkerator on 2007-06-02
I wanted to try out KDE, but finally realizing that it is a bit slow for me, although pretty, I should go back to Gnome. Now I just uninstalled KDE, but my desktop manager is still set to KDE, and at the logon screen I now have a regular Debian logon. Is there any way to switch Kdm back to Gdm?

---

### Post by merlinus on 2007-06-02
This page may help --

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

-merlin

---

### Post by Linkerator on 2007-06-02
> **merlinus said:**
> This page may help --

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

-merlin

This didn't work much, I just need to switch the default manager from kdm to gdm.

---

### Post by merlinus on 2007-06-02
At the login screen, there should be a clickable Session choice.  MIne is at the lower left.

From there, I can choose which windows manager to use, and after entering my username and password, I am prompted whether this is only for this session or to be the default.

-merlin

---

### Post by aysiu on 2007-06-02
> **Linkerator said:**
> This didn't work much, I just need to switch the default manager from kdm to gdm.
Log out

Press Control-Alt-F1

Log in

Type ```
sudo /etc/init.d/kdm stop
sudo nano -B /etc/X11/default-display-manager
``` Then change ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
``` and save (Control-X, Y, Enter). Finally ```
sudo /etc/init.d/gdm restart
``` This should bring GDM back to life. If not, press Control-Alt-F7

---

### Post by Linkerator on 2007-06-02
Great, it works perfectly now. And thanks to you too, merlinus. I got rid of those unnecessary packages that came with it.

---

