---
title: "Karmic login screen not showing shutdown/reboot options"
date: 2010-01-26
forum: Desktop Environments
---

### Post by mutex023 on 2010-01-26
I dont know what happened, but the power button icon in the login screen (see screenshot) which allows you to shutdown/reboot has disappeared.
I've tried completely removing gdm, human-theme packages, reinstalling them, running sudo dpkg-reconfigure etc...
nothing works.
This is very frustrating because I've to do ctrl+alt+F1 , login and then do a sudo reboot.
Any help will be much appreciated,
Thanks.

---

### Post by mutex023 on 2010-01-26
No ideas ? Anyone?

---

### Post by adam814 on 2010-01-26
Give this a try:
```
sudo dpkg-reconfigure devicekit-power
```

---

### Post by mutex023 on 2010-01-27
Nope, doesn't work.

---

### Post by nerdy_kid on 2010-01-27
could always try deleting all the (hidden) files in /root/ -- make a backup first though obviously.  Also maybe checking the config from gdms point of view:
```

sudo -i -u gdm

```

---

### Post by mutex023 on 2010-01-28
There are no config files for gdm in /root, I checked.
However there are certain files in /etc/gdm , but I dont know how to edit them.

---

