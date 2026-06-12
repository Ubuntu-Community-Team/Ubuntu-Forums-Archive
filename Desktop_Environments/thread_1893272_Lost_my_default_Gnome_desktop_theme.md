---
title: "Lost my default Gnome desktop theme"
date: 2011-12-09
forum: Desktop Environments
---

### Post by StepNjump on 2011-12-09
Hi,

I unfortunately installed 120508-MagIcons_0.3-0_all.deb package. It changed my icons everywhere.
Then I wanted to remove the package so I did the following

dpkg -l | grep magi*

The package was named magicons 

dpkg -P magicons

then I rebooted.

I was startled to see that the new icons were still there!

What should I do in order to revert back to my gnome default?

Note that I had previously installed Nautilus elementary 

[http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html](http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html)


If someone could help me, I would appreciate it a lot.

Thanks


Pete StepNjump

---

### Post by hhh on 2011-12-10
The package is actually called MagIcons (I know, weird), so...```
sudo apt-get purge MagIcons
```

You can also just delete the icons by removing the file MagIcons in ~/.icons, though that won't remove the program.

---

