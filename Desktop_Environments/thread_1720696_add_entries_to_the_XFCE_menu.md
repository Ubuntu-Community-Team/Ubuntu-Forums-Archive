---
title: "add entries to the XFCE menu"
date: 2011-04-03
forum: Desktop Environments
---

### Post by cccc on 2011-04-03
hi

I have Xubuntu with XFCE 4 installed.
Howto add additional entries to the XFCE menu?

---

### Post by BrokenKingpin on 2011-04-12
In XFCE 4.6 (which you are probably on unless you are running the 11.04 beta) you have to do it using config files, which I am not sure of off hand.

If you are running XFCE 4.8 you can use an editor like Alacarte.

---

### Post by hhh on 2011-04-12
Xfce 4.6 menu entries are located in /usr/share/applications (except for the login window entries, which are in /usr/share/gdm/applications). New entries need to be created via .desktop files by hand, and can be stored either in /usr/share/applications or in ~/.local/share/applications...
[http://wiki.xfce.org/howto/customize-menu#add_entries](http://wiki.xfce.org/howto/customize-menu#add_entries)

You can use a direct path to an icon or just use the icon name if it's stored in /usr/share/pixmaps

---

### Post by mike555 on 2011-07-26
You might try a menu editor made in java , not really made for xfce, but works....
[http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/)   ... just download and put in your /home folder, uncompress and make the .jar file executable and set to open in jre .........

---

