---
title: "Unable to load desktop"
date: 2008-09-10
forum: Desktop Environments
---

### Post by shantanu kulkarni on 2008-09-10
I am unable to load the desktop in Ubuntu. The wallpaper does not load and I can not right-click on the desktop.

---

### Post by forger on 2008-09-10
1) What did you do or what were you doing/installing?

2) Try restart your pc:
 - press CTRL+ALT+F1
 - login
 - type: ```
sudo reboot
```
 - login in gnome, is it working now?

3) maybe restart nautilus?
 - press ALT+F2
 - does it open the "run application" window?
 - type:```
killall -9 nautilus
```
 - press ALT+F2 again and type:
```
nautilus
```

4) You can temporarily create another user:
 - press CTRL+ALT+F1
 - login
 - type: ```
sudo adduser newuser
```
 - fill in the details (password, name etc.)
 - once you're done, restart your pc: ```
sudo reboot
```
 - login using your new username

---

