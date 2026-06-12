---
title: "[SOLVED] how to stop xserver on kubuntu kde4?"
date: 2008-08-23
forum: Desktop Environments
---

### Post by kef_kf on 2008-08-23
how do i stop xserver on kubuntu kde4.1? typing in
```
sudo /etc/init.d/kdm-kde4 stop
```
returns
```
grep: /usr/lib/kde4/etc/kde4/kdm/kdmrc: No such file or directory Stopping K Display Manager: kdm-kde4 not running (/var/run/kdm-kde4.pid not found).
```

im trying to install nvidia binary driver and im not interested in using the packages or envy.

thanks

---

### Post by Diabolis on 2008-08-23
If you press **<Ctrl><Alt>backspace** it will kill xserver and it will log you out. Then you can press **<Ctrl><Alt>F1**, it will take you to a command line from where you can log in and do whatever you want without xserver running.

When you are done you can press **<Ctrl><Alt>F7** to go back to the graphical mode.

F1-F6 are terminals (tty)
F7 will show you the log in screen again

---

### Post by Shazaam on 2008-08-23
Try this (leave out -kde4).....
```
sudo /etc/init.d/kdm stop
```

---

### Post by kef_kf on 2008-08-23
> **Diabolis said:**
> If you press **<Ctrl><Alt>backspace** it will kill xserver and it will log you out. Then you can press **<Ctrl><Alt>F1**, it will take you to a command line from where you can log in and do whatever you want without xserver running.

When you are done you can press **<Ctrl><Alt>F7** to go back to the graphical mode.

F1-F6 are terminals (tty)
F7 will show you the log in screen again

thanks, this did the trick

---

