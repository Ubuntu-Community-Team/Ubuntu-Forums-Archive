---
title: "Graphical Login Issues"
date: 2008-05-27
forum: Desktop Environments
---

### Post by jjrev on 2008-05-27
I'm running 8.04 with all the latest updates.  When I try to login, I only get my wallpaper, nothing else seems to work.  I have to change my session to the "Gnome Defaults" in order for Gnome to start properly.  It seems like some of the startup scripts are not being executed properly(?)

Has anyone experienced this?  Where do I start if I want to debug this?

---

### Post by overdrank on 2008-05-27
> **jjrev said:**
> I'm running 8.04 with all the latest updates.  When I try to login, I only get my wallpaper, nothing else seems to work.  I have to change my session to the "Gnome Defaults" in order for Gnome to start properly.  It seems like some of the startup scripts are not being executed properly(?)

Has anyone experienced this?  Where do I start if I want to debug this?
HI and you could try using the keys ctrl, alt, F1 and then the command 
```
sudo /etc/init.d/gdm restart
```
And please do not make multiple threads on the same issue.
[http://ubuntuforums.org/showthread.php?p=5054976#post5054976](http://ubuntuforums.org/showthread.php?p=5054976#post5054976)

---

