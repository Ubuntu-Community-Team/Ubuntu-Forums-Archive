---
title: "[SOLVED] KDE su password on gnome ubuntu"
date: 2008-10-03
forum: Desktop Environments
---

### Post by k3kiaze on 2008-10-03
Hi,

Running Ubuntu 8.04 with gnome login.(default for everyone). I installed KDM theme manager from synaptec to customize my KDE apps (amarok, juk, k3b .. etc,). When I launch KDE theme manager, it says I have to click "administrator mode" to make changes, and it's asking me for a KDE su password, and its not accepting me gnome password.

The Launcher command for this program is "kcmshell kdmtheme" when i type "kcmshell" in terminal i get this: 

```
kcmshell
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
DCOP Cleaning up dead connections.
Usage: kcmshell [Qt-options] [KDE-options] [options] module 
```

I guess I need to setup a su password for KDE like i did after installing ubuntu first time. Anyone know how?

---

### Post by p_quarles on 2008-10-04
Try this:
```
echo -e "[super-user-command] \nsuper-user-command=sudo" >> ~/.kde/share/config/kdesurc
```
At that point, kdesu should authenticate your main user's account as a sudoer, rather than looking for the root password. This is set up automatically if you install Kubuntu, but apparently not by adding parts of KDE.

Also, I should point out that kdm-theme-manager has nothing whatsoever to do with the appearance of KDE programs. It only themes the KDE login/display manager, KDM. It's also broken.

---

### Post by k3kiaze on 2008-10-04
> **p_quarles said:**
> I should point out that kdm-theme-manager has nothing whatsoever to do with the appearance of KDE programs.

That was exactly what I was trying to do! what a waste. How can I change KDE program appearances without install the whole KDE shebang?

---

### Post by k3kiaze on 2008-10-09
Solved by installing kcontrol pkg from synaptec. It will install many other KDE control tools.

---

### Post by go_beep_yourself on 2008-11-24
Does anybody know how to get kcontrol in Ubuntu 8.10?

---

