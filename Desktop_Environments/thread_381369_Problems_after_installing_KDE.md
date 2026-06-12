---
title: "Problems after installing KDE"
date: 2007-03-10
forum: Desktop Environments
---

### Post by legendarysock on 2007-03-10
Hey everyone.
I installed KDE components today to get the wonderful kxdocker program. I followed this guide: [http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake), except I'm using Edgy not Dapper. Anyway, I had some problems with the kxdocker program. If i started it up, it would crash on me after some graphical issues. I tried restarting my computer (I'm new to Linux, I didn't know what else to do, so I tried that first), but when I restarted, I was greeted by a CLI login screen :(  I logged in and then tried startx, but KDE rather than Gnome started up :confused: . I need help getting GDM back as well as my Gnome desktop environment. Thanks in advance :)

---

### Post by teaker1s on 2007-03-12
> Uninstall KXDocker

Go to each directory you installed it and type:

make clean && sudo make uninstal [QUOTE]

you have kdm you can select default session as gnome, but you want  gdm back so
```
sudo dpkg-reconfigure gdm
```

---

