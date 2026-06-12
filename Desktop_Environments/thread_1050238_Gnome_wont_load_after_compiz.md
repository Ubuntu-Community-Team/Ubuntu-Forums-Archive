---
title: "Gnome wont load after compiz"
date: 2009-01-25
forum: Desktop Environments
---

### Post by kshea88 on 2009-01-25
Hello all I'm a pretty new ubuntu user (about a month) and haven't had any problems until now.  I was playing around with my compiz settings and when I opted to allow the zoom feature (full area zoom I think it was called) my computer froze for a few seconds and sent me back to the login screen.  Every time I try to login in Gnome it will start to load for a few seconds then my screen will go blank and send me back to the login screen.  Kde works fine and I am writing this with the same computer.  Not sure what to do here kde is nice, but I like the feel of Gnome better.  Can I just uninstall and reinstall Gnome under kde?  Thanks in advance.

---

### Post by gettinoriginal on 2009-01-25
At your grub splash, do you have an option to go to CL ??  If you do, then enter this, it will reset compiz to default settings which should let you back into gnome:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by kshea88 on 2009-01-25
Awesome it worked, thanks.

---

