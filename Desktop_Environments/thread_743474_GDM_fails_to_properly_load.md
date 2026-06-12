---
title: "GDM fails to properly load"
date: 2008-04-02
forum: Desktop Environments
---

### Post by Ryoushi19 on 2008-04-02
I'm running 8.04, and generally, I've had little trouble, until now.  The problem I'm having now is completely destructive, and until it's fixed, my copy of Ubuntu is unusable.  Whenever I try to boot, GDM pops up as if it's going to load a login screen, and sits there. ...and sits there...and sits there some more.  It keeps showing the loading cursor and never loads anything.  What's wrong with it?  Any way it can be fixed?

---

### Post by benerivo on 2008-04-02
You could try reinstalling gdm from the console, and if that doesn't work then try another login manager as a temporary fix. To try reinstalling, press Ctrl+Alt+F2 when gdm is hanging and then```
sudo apt-get --reinstall install gdm

```then reboot. If that fails, then you could try```
sudo apt-get install xdm
``` in the same manner, and this should let you select xdm as your deafult login manager. Then reboot or these commands might be quicker```
sudo killall gdm
```and```
sudo /etc/init.d/xdm start
```

---

### Post by Ryoushi19 on 2008-04-03
Hey, your suggestion fixed it ^.^.  One upgrade and a few minutes later, GDM is booting beautifully, so thanks much.  I would have done an upgrade, but I tried to do it in recovery, which was impossible, due to the fact that recovery has no internet.  So thanks much for teaching me about Ctrl+Alt+F2.  :)

---

### Post by JustinAlf on 2008-04-04
I have the same problem, except that I cannot download or reinstall gdm

It tells me that it cannot get to the Ubuntu Repositories

Can I re-install GDM fromt he CD, if so how?

---

### Post by $imp$ on 2008-04-23
I had the same problem.  I had to uninstall and then reinstall gnome.  Reinstalling it only did not work.

---

