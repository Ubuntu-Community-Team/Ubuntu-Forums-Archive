---
title: "Gnome menu"
date: 2009-05-29
forum: Desktop Environments
---

### Post by tamal.nath@gmail.com on 2009-05-29
Hi All,

I have found a method by which we can edit gnome menu without using standard menu editor (alacarte) that can be found at System -> Preferences -> Main Menu. I didn't use it as it makes changes for the current user only (Changes are saved in /home/<user>/.config/menus/). :( But to make changes applicable to all user I have updated the following files:
[LIST]
/etc/xdg/menus/oraclexe.menu
/usr/share/desktop-directories/oraclexe-10g.directory
/usr/share/gnome/vfolders/oraclexe-10g.directory
[/LIST]

I was just trying to change the menu. ;) But if you want to change a menu item, then you have to edit:
/usr/share/applications/*.desktop

---

