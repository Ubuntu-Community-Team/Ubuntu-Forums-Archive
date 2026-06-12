---
title: "Can't log in- Log in screen just appears again"
date: 2011-08-26
forum: Desktop Environments
---

### Post by dsavi on 2011-08-26
Edit: SOLVED. See the end of this post.

First of all I'd like to mention that I'm by no means new to Ubuntu, I've been using it since 2008. So there's a reason I'm posting here.

Starting yesterday, whenever I try to log in to Ubuntu 11.04, if I put in the right password it just turns my monitors on and off again and shows me the login screen. I tried switching sessions (I use Unity 2D daily build), I tried installing Lightdm and kdm but they do exactly the same thing. I tried restarting the display managers (CTRL+ALT+F1, logging in in text mode and sudo service gdm/kdm/lightdm restart).

Thanks for any help.


**I solved this problem by accident.** I had given up and was just going to reinstall Ubuntu. Before I did that, I backed up my /home/<username> directory onto Windows, but because it was so full, I decided to delete everything but what I needed. I'm **not sure** which directory or config file I deleted that did it, but here are the directories/config files that I deleted: (I removed some directories that I know didn't cause the problem from this list, just to save you some time)

```
rm -rf .cache .compiz .config .dbus .gksu.lock .gnome2 .gnome2_private .ICEauthority .icedtea .local .mission-control .nautilus .nv .pki .profile .pulse .pulse-cookie .sesi_licenses.pref .Xauthority .xsession-errors .xsession-errors.old 
rm -rf .esd_auth .dmrc 
rm -rf .gconf .gconfd

```

Hope that helps!

---

### Post by drpjkurian on 2011-08-26
Hi
Try using **oem** as username and enter your password.

---

### Post by dsavi on 2011-08-26
I'm afraid that didn't work. Just gave an authentication error.

---

