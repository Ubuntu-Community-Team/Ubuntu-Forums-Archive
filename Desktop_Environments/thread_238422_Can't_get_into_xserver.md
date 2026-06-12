---
title: "Can't get into xserver"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Donnut on 2006-08-17
Hi all.  I changed a setting in ubuntu login screen preferences, now all I see in the login screen is "Network boot".  From here I can not get into my normal login screen.  I try to boot into recovery mode, login as steve(user) and get this error: 

xauth:  creating new authority file /home/steve/.serverauth.4019
X: user not authorized to run the X server, aborting.
xinit:  Server error.

What can I do?

---

### Post by murataht on 2006-08-17
try to boot with recovery mode, and add a new user with adduser command as root. reboot and login into gdm with the new user. if this is not working either, maybe the gdm configuration has something wrong. 

good luck

murat

---

