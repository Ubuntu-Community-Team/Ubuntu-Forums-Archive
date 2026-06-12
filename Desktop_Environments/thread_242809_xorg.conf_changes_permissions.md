---
title: "xorg.conf changes permissions"
date: 2006-08-24
forum: Desktop Environments
---

### Post by stepheny on 2006-08-24
I made some changes to xorg.conf which prevented xwindows from opening. Luckily I had save the original xorg.conf as xorg_orig.conf in /etc/X11. So I booted in rescue mode and renamed the xorg_orig.conf to xorg.conf using mv. I rebooted and got as far as the login screen but after entering my username and password I get an error message saying something to the effect that some child processes cannot be launched. I rebooted into rescue and noticed that the permissions for my home directory had been changed to owner = 1000. I corrected this using the chown -R command and rebooted but the error message remains.

Does anyone know what is causing this?

Thanx

---

