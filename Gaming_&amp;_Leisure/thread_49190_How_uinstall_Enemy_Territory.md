---
title: "How uinstall Enemy Territory??"
date: 2005-07-15
forum: Gaming &amp; Leisure
---

### Post by peter07 on 2005-07-15
How uinstall Enemy Territory??

---

### Post by endy on 2005-07-15
Unless you installed it to a different directory this should work:

```

sudo rm -rf /usr/local/games/enemy-territory/
sudo rm -rf /usr/share/gnome/apps/Games/et.desktop

```

This deletes the game directory and the gnome menu entry. You can get rid of any game settings stored in your home directory by:

```

rm -rf ~/.etwolf

```

That should delete everything ET on your system :)

---

### Post by peter07 on 2005-07-15
Thanks - but I have still problem.

I can't delete links. 

> 
sudo rm -rf /usr/share/gnome/apps/Games/et.desktop

That folder doesn't exist. I still have enemy-territory in application list.

Why they don't make a simple uinstaller ??

---

### Post by endy on 2005-07-15
hmm, thats where the installer puts the links for me... :S  Anyway just open a terminal and type:

```

locate et.desktop

```

You should see where it is stored then just delete it :)

---

### Post by Caboto on 2005-07-15
Try searching a et.desktop file in your home directory....
by me it's ~/.gnome2/vfolders/applications/et.desktop
Deleting that file, should remove the entry in your menu. Alternatively you could try Smeg instead...

---

### Post by peter07 on 2005-07-15
No result :(

---

### Post by peter07 on 2005-07-16
Finaly I've located deskop file. It was **enemy-territory.deskop**

But enemy-territory is still in application-list ( MENU-Application-Run-Application) and in Debian menu ( MENU-Application-Debian-Games ).

How remove et from this locations ???


EDIT.

I've just deleted enemy-territory.desktop from:

> /var/lib/gnome/Debian/Games
and
> /var/lib/menu-xdg/applications/menu-xdg/

After uptade-menus command - links are still in menus?? WHY ??


EDIT

I find some more et-files and I've deleted them. Now I hav'nt got any ET links :)

---

