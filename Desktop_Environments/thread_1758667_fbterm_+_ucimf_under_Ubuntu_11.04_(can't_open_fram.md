---
title: "fbterm + ucimf under Ubuntu 11.04 (can't open frame buffer device; segmentation fault"
date: 2011-05-14
forum: Desktop Environments
---

### Post by olcolc on 2011-05-14
Made the following commands:

 $ sudo aptitude install fbterm 
$ sudo aptitude install libucimf0 fbterm-ucimf ucimf-openvanilla openvanilla-imgeneric fbterm

Run: LC_CTYPE=zh_TW.UTF-8 fbterm -i fbterm_ucimf

System returns: 
can't open frame buffer device!
Segmentation fault

Additional information:
-Ubuntu 11.04 under wubi install 
-user already added to video group (checked "User and Group" )

Thanks for your help!

---

### Post by phoenix201 on 2011-05-30
just try to start fbterm with sudo. this should fix your problem. If you don't want to run fbterm always as sudo perhaps the modification of the permissions for your /dev/fb0 could fix that.

---

