---
title: "GDM is not running? Yes it is."
date: 2007-10-19
forum: Desktop Environments
---

### Post by CulleyS on 2007-10-19
When I run "gdmsetup" I get an error that GDM is not running.  Well, it appears to be.  I'm in a Gnome Desktop Environment.  But not all of my Gnome Applications are showing up.  In fact, it looks like a bunch of KDE applications have replaced them.

But, when I go into System > Administration > System Monitor, I look at processes and system info and only see gnome environments/apps.  See attached Screenshot.

I have both kubuntu and ubuntu desktop environments installed.  When I boot up, I'm taken to the KDE default login screen, but my session default is set to Gnome.

Thanks in advance for any help.

---

### Post by btt on 2007-10-19
Sounds to me like when you installed KDE, it replaced gdm with kdm as your default login app.  This means gdm will not run at startup, as it only executes if it's set as default.

```
sudo echo "/usr/sbin/gdm" >> /etc/X11/default-display-manager
```

should do the trick.

---

### Post by CulleyS on 2007-10-19
That did it, thanks.  I couldn't remember where that file was located or what it was called, so had no clue how to search for it. :)

---

