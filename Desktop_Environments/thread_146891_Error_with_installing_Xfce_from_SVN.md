---
title: "Error with installing Xfce from SVN"
date: 2006-03-19
forum: Desktop Environments
---

### Post by draye on 2006-03-19
I download Xfce from SVN, while installing xfce4-dev-tools and after command ./configure I have this error:

> checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0... Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.



I use ubuntu 5.10 and I have gtk2 i glib. How to change PKG_CONFIG_PATH and add this directory?

---

### Post by dermotti on 2006-03-19
Why not just download it with apt-get?

---

### Post by draye on 2006-03-19
Xfce from svn is more stable, have a lot of change, You can do bettter themes etc...
  Xfce from svn can be more buity: :) [http://www.gentoo.pl/~arsen/screens/xfce4-new/xfce4-20060220.png](http://www.gentoo.pl/~arsen/screens/xfce4-new/xfce4-20060220.png)
[http://www.gentoo.pl/~arsen/screens/xfce4-new/xfce4-20060205.png](http://www.gentoo.pl/~arsen/screens/xfce4-new/xfce4-20060205.png)

---

### Post by ranf on 2006-03-19
[QUOTE=draye]
I use ubuntu 5.10 and I have gtk2 i glib. How to change PKG_CONFIG_PATH and add this directory?[/QUOTE]

Look at this Wiki page:
[https://wiki.ubuntu.com/CompilingEasyHowTo](https://wiki.ubuntu.com/CompilingEasyHowTo)

---

