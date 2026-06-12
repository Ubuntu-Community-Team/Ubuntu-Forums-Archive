---
title: "[SOLVED] Cannot switch back to gdm login"
date: 2008-08-10
forum: Desktop Environments
---

### Post by edog76 on 2008-08-10
Just installed kubuntu and set the login screen to kdm. I want to switch back to gdm and have run both:
```

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure kdm

```
selecting gdm both times, but login screen is still kdm. In addition, kde will not load. Instead my gnome desktop loads. I also cannot select "restart" or "shut down" from gnome. If I want to do that, I have to log out (to kdm) then select it from there. Help!

---

### Post by SunnyRabbiera on 2008-08-10
well you can remove kdm and re install gdm.

---

### Post by edog76 on 2008-08-10
okay, and are the correct commands:
```

sudo rm kdm
sudo apt-get install gdm

```

---

### Post by benerivo on 2008-08-10
If you install any login/display manager you should get questioned on which one you want to use. So i would run```
sudo apt-get install xdm
```and then choose gdm as your default. You'll then be free to```
sudo apt-get purge kdm && sudo apt-get purge xdm
```You can also check (and change) which display manager is your default with```
sudo nano /etc/X11/default-display-manager
```

---

### Post by edog76 on 2008-08-10
:redface: Apparently I never restarted the computer after switching back to gdm.  All clear now.

---

