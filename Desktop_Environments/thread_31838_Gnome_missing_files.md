---
title: "Gnome missing files"
date: 2005-05-04
forum: Desktop Environments
---

### Post by Amdmhz on 2005-05-04
HI all.. I really don't understand how I can be missing Gnome files but everytime I try to install this program it tells me gnome-vfs-2.0 can not be found, so I download gnome-vfs-2.0 and then that program tells me that gconf is need, then I install gconf and try to reinstall gnome-vfs-2.0 and it tells me gconf can't be found. Very bazzar... 

Anyway, all I am trying to do is install SyncCe so that I can use my PDA. SyncCE supports Both Gnome and KDE., but in KDE I run into the same problems.

Does anyone know of a different PDA program I can try?

Thanks for the help.

---

### Post by Amdmhz on 2005-05-05
Here is an example: I need to is sync-rra for my PDA to work. When I build it from source and do ./configure I get:

checking for mdir_parse in -lmimedir... no
configure: error: Can't find libmimedir ([http://sourceforge.net/projects/libmimedir/](http://sourceforge.net/projects/libmimedir/))

When I  apt-get install libmimedir
Reading package lists... Done
Building dependency tree... Done
libmimedir is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

I don't understand it. Other people have used syncCE in ubuntu and have gotten it to work. I have no idea what I did wrong?

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=Amdmhz]Here is an example: I need to is sync-rra for my PDA to work. When I build it from source and do ./configure I get:

checking for mdir_parse in -lmimedir... no
configure: error: Can't find libmimedir ([http://sourceforge.net/projects/libmimedir/](http://sourceforge.net/projects/libmimedir/))

When I  apt-get install libmimedir
Reading package lists... Done
Building dependency tree... Done
libmimedir is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

I don't understand it. Other people have used syncCE in ubuntu and have gotten it to work. I have no idea what I did wrong?[/QUOTE]


If you are building apps from source, you need to have not just binaries but also source files for gnome libraries. They are in so-called development (-devel) packages. So you need not only gconf but also gconf-devel, and so on.

---

### Post by Amdmhz on 2005-05-05
Alex,

Thanks for your help...I seem to be getting closer. The program I am missing now is called liborange. I did an apt-get and downloaded and installed everything that it needed. I get this when I try to install the last package:

checking for orange_squeeze_file in -lorange... no
configure: error: Can't find orange library

I don't think there is a dev for this one. Any ideas? 

Thanks

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=Amdmhz]Alex,

Thanks for your help...I seem to be getting closer. The program I am missing now is called liborange. I did an apt-get and downloaded and installed everything that it needed. I get this when I try to install the last package:

checking for orange_squeeze_file in -lorange... no
configure: error: Can't find orange library

I don't think there is a dev for this one. Any ideas? 

Thanks[/QUOTE]
 Sorry - can't help here. Never heard of this one.

It does happen sometimes that apps do not install their libraries in expected location, or do not register them properly (I do not know what "properly" is myself), creating all kinds of problems. This, of course, means that the app writer did a poor job. It may be such a case - or maybe not.

---

