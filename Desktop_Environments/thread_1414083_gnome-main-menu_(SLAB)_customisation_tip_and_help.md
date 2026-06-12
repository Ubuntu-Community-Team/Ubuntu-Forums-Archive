---
title: "gnome-main-menu (SLAB) customisation tip and help"
date: 2010-02-23
forum: Desktop Environments
---

### Post by megamaced on 2010-02-23
Hi,

I have managed to customise the gnome-main-menu (SLAB start menu) panel by changing the default "Computer" name to "Ubuntu" and changing the generic computer icon to the Ubuntu logo by editing the file /usr/share/gnome-main-menu/slab-window.glade and doing a find and replace, changing every word "Computer" to "Ubuntu" and changing every word "gnome-fs-client" to "gnome-main-menu".

Now I would like to add a shortcut to Synaptic Package Manager to the right hand side of the Menu (under System - perhaps under Control Centre) and call it something like "Install Software" (like in SUSE). I can see I need to edit the file /usr/share/gnome-main-menu/system-items.xbel and I have changed pre-saved "install software" entry to point to the synaptic.desktop file but it still doesn't show in the menu so I probably haven't done it right.

Can anyone help?

---

### Post by kerry_s on 2010-02-23
it's simple drag & drop. add synaptic to your favorites then drag & drop it on that side panel then you can remove it from favorites.

if i remember right, you can also just drag & drop right on the panel botton.

---

### Post by megamaced on 2010-02-23
LOL I didn't think it would be so simple!!

The applications in the Control Center chooser do not have the "Add to Favourites" right click option but I managed to add Synaptic to my favourites by just clicking and dragging Synaptic from the Control Center directly onto the "start" button!

Thanks!

---

### Post by megamaced on 2010-02-25
Another question!

The default Ubuntu places menu has a "Connect to server" shortcut. This functionality is lost in gnome-main-menu. How can I create a shortcut to connect to server?

Thanks

---

### Post by kerry_s on 2010-02-25
create a *.desktop file for it in ~/.local/share/applications then drag & drop it on the menu button, once in your favorites you can move it where you want.

example desktop file:

```
[Desktop Entry]
Encoding=UTF-8
Name=Connect to server
Exec=the command
Icon=some.png
```

ps: have you tried linux mint, it has a pretty good slab menu, same easy drag & drop features, plus other kinds of settings. i'm downloading version 8 now to install, just killing time on the forum till it's done downloading. :)
[http://www.linuxmint.com/rel_helena_whatsnew.php](http://www.linuxmint.com/rel_helena_whatsnew.php)

---

### Post by kerry_s on 2010-02-25
here's what the default mint slab looks like.

---

### Post by megamaced on 2010-02-25
Ok thanks but do you know what the exec will be?

---

### Post by kerry_s on 2010-02-25
sorry for the wait, had to sleep. ;)
i just now installed ubuntu 9.04, didn't like the way linux mint 8 felt & ubuntu 9.10 is just wacked on my system.

press-> alt+f2
type-> gedit ~/.local/share/applications/connect.desktop
put:

```
[Desktop Entry]
Encoding=UTF-8
Name=Connect to server
Exec=nautilus-connect-server
Icon=system-run.png
```


i'm not totally sure, cause i'm still half a sleep, working on my first cup of coffee now, but just a quick look, that's what i would try.

---

