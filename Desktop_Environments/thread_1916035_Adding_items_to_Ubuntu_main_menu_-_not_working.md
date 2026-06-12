---
title: "Adding items to Ubuntu main menu - not working"
date: 2012-01-27
forum: Desktop Environments
---

### Post by robson22 on 2012-01-27
Welcome.
First thing is sorry about my english.
From a few days im trying add new item to to Ubuntu main menu, i reading tens of threads about it on ubuntu forum and other disto forums, additionally few tutorials and nothing, i cant add new menu or new item. Im trying it on on these system version:
Ubuntu 11.04 - Gnome 2.32.1
Ubuntu 10.04 - Gnome 2.30.2
Kubuntu 11.04
When i run alacarte RMB on the menu and choose "Edit Menus" or with root account with "sudo alacarte"(when editing console not show any errors), when i add new menu or item i mark it to show in main menu this settings not saving. In the main menu new menu or item not show, when i run alacarte again my new menu/item is unmarked. What is interesting when im unmark/mark items which are installed which ubuntu for example: LibraOffice then everything is ok they disapper/they are in main menu, only new menu/item, only new item/menu which i create dont show in main menu.
Im already try change the permission rights which this advice > [http://ubuntuforums.org/showthread.php?t=1476034](http://ubuntuforums.org/showthread.php?t=1476034) and this not help.
Im trying manualy add menu by this tutorial > [https://wiki.matusov.sk/?id=howto/gnome-menu-edit](https://wiki.matusov.sk/?id=howto/gnome-menu-edit) and also dont working.

Please help.

I greet

---

### Post by Krytarik on 2012-01-27
Notice two things:

[LIST]
[*]If you edit the menus as root, it won't affect the menus of your user (btw., use "gksudo" for graphical apps when really needed, details [here]("http://www.psychocats.net/ubuntu/graphicalsudo")).
[/LIST]

[LIST]
[*]When you create a new sub-menu, it must contain at least one launcher to eventually show up in the menu.
[/LIST]
Hope this helps already.

---

### Post by robson22 on 2012-01-27
This realy help. Thanks :D

---

