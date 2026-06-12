---
title: "LightDM not unlocking the GNOME keyring"
date: 2012-10-06
forum: Desktop Environments
---

### Post by Borromini on 2012-10-06
I have installed the 12.10 beta and replaced Unity with Openbox.

I have gotten the brightness, volume keys etc. to work by adding gnome-keyring-daemon and gnome-settings-daemon to Openbox's environment file, but I am unable to get my keyring unlocked upon login (on Unity, this used to work and I'd have my SSH and GPG keys loaded).

I have been digging through the documentation ([this](http://askubuntu.com/questions/150487/what-happens-under-the-covers-to-log-me-in-and-start-up-the-unity-graphics-user) amongst others) and have grepped the /etc/pam.d/* files for gnome keyring stuff. Everything looks to be there (I did not touch those after or during switching from Unity to Openbox. Yet I have to unlock my keys every time again after login. Been looking in /var/log/lightdm/lightdm.log as well, no pointers on SSH/GPG keys.

Anybody know how to get this to work?

---

### Post by Borromini on 2012-10-30
Anyone? In the meantime I updated to 12.10 stable, but no dice.

---

