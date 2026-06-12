---
title: "Manually install a sincgle icon"
date: 2006-09-26
forum: Desktop Environments
---

### Post by hoagie on 2006-09-26
I just want to change the firefox icon. I did this by replacing the firefox.png icon in the usr/share.pix...  (I don't remember the rest) but that only applied in the human theme (and every other theme that comes with ubutnu). Any ideas?

---

### Post by CatKiller on 2006-09-26
> **hoagie said:**
> I just want to change the firefox icon. I did this by replacing the firefox.png icon in the usr/share.pix...  (I don't remember the rest) but that only applied in the human theme (and every other theme that comes with ubutnu). Any ideas?

You could try calling your file firefoxnew.png and saving it in /usr/share/pixmaps, and then typing the following command into the Terminal```
gksudo gedit /usr/share/applications/firefox.desktop
```Then find the line that starts Icon= and change that to /usr/share/pixmaps/firefoxnew.png

I think that that should change the icon for you, regardless of theme.

---

### Post by CatKiller on 2006-09-26
Actually, I think that that will change the icon for all users regardless of theme, so it might not be what you want. But you can edit the menu item (right-click on the menu, select Edit Menus) so that it uses your icon instead.

---

### Post by hoagie on 2006-09-26
> **CatKiller said:**
> You could try calling your file firefoxnew.png and the Terminal```
gksudo gedit /usr/share/applications/firefox.desktop
```Then find the line that starts Icon= and change that to /usr/share/pixmaps/firefoxnew.png

theme.

Em where's that line?

---

### Post by hoagie on 2006-09-26
Got it but it didn't work

---

### Post by CatKiller on 2006-09-26
You might need to refresh the panel for changes to show up:```
sudo killall gnome-panel
``` Or it might be using a different .desktop file in your Home folder, just for you. Who knows? I haven't managed to get my head around which configuration gets used in a multi-user environment with themes yet. Just do it through the menu, and it should be the configuration that it's using that gets changed. If you want to change panel icons as well, then you'll have to edit the appropriate .desktop file in  ~/.gnome2/panel2.d/default/launchers/ as well. And refresh the panel afterwards.

---

### Post by hoagie on 2006-09-26
Nothing works, arg never mind
:twisted:

---

