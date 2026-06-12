---
title: "Missing shutdown button in KDE"
date: 2008-04-29
forum: Desktop Environments
---

### Post by krojew on 2008-04-29
I've installed Kubuntu 8.04 and I have a problem. Shutdown and restart buttons are missing from KDE. There is only a Logout button. I've searched for a solution but found only other reports. Can anybody help?

---

### Post by Zorael on 2008-04-29
Go into System Settings, then Advanced tab, then Session Manager. Check 'offer shutdown options'.

---

### Post by krojew on 2008-04-29
It is checked, but still the buttons are missing.

---

### Post by Zorael on 2008-04-29
Tried this?
> **Obor said:**
> Its because GDM is your default display manager (both gnome and xfce use GDM).

It's a confirmed [bug in kdebase]("https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695"). KDE is not talking to GDM...

You can change your display manager to KDM 
```
sudo dpkg-reconfigure gdm
```
and then you will have those buttons in KDE but they will be missing in gnome and Xfce :(

The best is probably to use
shutdown
```
sudo shutdown -h now
```
restart
```
sudo shutdown -r now
```
And wait till they fix the bug.

---

### Post by krojew on 2008-04-30
Yes I did. Didn't help.

---

