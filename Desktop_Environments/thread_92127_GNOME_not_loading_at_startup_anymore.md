---
title: "GNOME not loading at startup anymore"
date: 2005-11-18
forum: Desktop Environments
---

### Post by Stenger on 2005-11-18
I just get prompted for a username and password.  I can use the startx command to get GNOME up, but I don't want to have to.  Anyone know how I can fix?  Thanks in advance!!!

---

### Post by schdefan on 2005-11-18
Is gdm (the login manager) running?
> ps - A  | grep gdm
You have to check if there is a link in /etc/rc5.d to gdm.
If not run > sudo update-rc.d gdm defaults 98 2 to at the link that gdm is started at boot time.
schdefan

---

### Post by rosslaird on 2005-11-18
Or, another way (for non-geek gurus) is to run two commands:

"sudo rcconf" (you may have to install rcconf from apt first) -- choose gdm
"sudo dpkg-reconfigure gdm" (or kdm) -- choose gdm

Reboot.
It should work.

Ross

---

