---
title: "Can't delete menu items"
date: 2006-05-31
forum: Desktop Environments
---

### Post by kinghajj on 2006-05-31
I'm trying to delete a menu item with the Alacarte Menu Editor, but I can't. I even ran the program with sudo and couldn't delete items.

---

### Post by philipacamaniac on 2006-05-31
I've only ever been able to hide menu items of installed programs. I can, however, delete items of uninstalled programs that apparently forgot to remove their menu item, and I can delete menu items that I added myself.

---

### Post by jocko on 2006-05-31
The starters (.desktop files) that are listed in the menus can be found in:
/home/username/.local/share/applications/
and
/usr/share/applications/
(don't know if there are more in any other places)

I guess this could work:
1. inactivate the items in alacarte
2. restart the panel
```
killall gnome-panel
```
3. change the filename of the ones you want to get rid of:
```
mv ~/.local/share/applications/appname.desktop ~/.local/share/applications/appname.desktop.old
```
and/or:
```
sudo mv /usr/share/applications/appname.desktop /usr/share/applications/appname.desktop.old
```
4. To revert, just rename them to their correct filenames again.
5. Don't blame me if you mess it up, I am not an expert... :)

---

