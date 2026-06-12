---
title: "Splash Screen Freeze"
date: 2009-01-20
forum: Desktop Environments
---

### Post by beers on 2009-01-20
Hello.
I was messing around with XFCE, and enabled the splash screen after login.  Now, whenever I try to login in any type of desktop environment (I've tried XFCE, KDE, and Gnome, all have the same issue), the splash screen comes up and hangs the system, eventually exhausting it of memory.  Is there any way to disable this from console?  If I don't login I can ctrl+alt+f2 and everything seems peachy from there (using links to post this, hah).  I'd just like to have a GUI again :( .  Thanks in advance.

---

### Post by beers on 2009-01-20
```
sudo apt-get purge gdm kdm ubuntu-desktop xubuntu-desktop kubuntu-desktop
```
and then reinstall seemed to do the trick. :D
Sorry, I'm new  ;)

---

### Post by beers on 2009-01-20
or not lol.

Although once I kill the gdm process and am logged in console I can boot to gnome with no problems.  Any idea how to get rid of that XFCE splash though?  :P

---

