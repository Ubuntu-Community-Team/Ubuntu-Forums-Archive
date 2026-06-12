---
title: "Replace Kwin with openbox"
date: 2006-12-13
forum: Desktop Environments
---

### Post by Frak on 2006-12-13
Does anybody know how to replace Kwin/KDM with openbox?

---

### Post by pay on 2006-12-14
Look here [http://gentoo-wiki.com/HOWTO_Openbox#Standalone_Openbox](http://gentoo-wiki.com/HOWTO_Openbox#Standalone_Openbox)

---

### Post by aysiu on 2006-12-14
This may help:
[http://developer.kde.org/~seli/kdewm/](http://developer.kde.org/~seli/kdewm/)

---

### Post by Frak on 2006-12-14
Thanx, I thought nobody would attempt to answer this, but appearantly I was wrong thanks!

EDIT
Figured it out
```
sudo kate /etc/X11/xinit/xinitrc
```
then when inside the file
```
# Startup stuff for X

# Make openbox the KDE window manager
export KDEWM=openbox

# Make KDE system tray apps work
kdetrayproxy &

# Start the KDE environment
startkde
```

---

