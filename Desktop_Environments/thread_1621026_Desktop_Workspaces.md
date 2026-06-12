---
title: "Desktop Workspaces"
date: 2010-11-13
forum: Desktop Environments
---

### Post by sr_guy on 2010-11-13
Running Ubuntu 10.04 64bit.

Is there a way to setup each workspace to have different icons on each workspace.  Example:

Workspace 1 = Internet icon stuff (IM, Browsers, Etc...)
Workspace 2 = Multimedia icons (Video Editors, Music Clients)

And so on....


Is this possible?

---

### Post by thegammaray on 2010-11-14
By default, Ubuntu (and Gnome in general, AFAIK) uses Nautilus to draw the desktop, which includes wallpaper and desktop icons. Nautilus does not support different content on different desktops.

However, Ubuntu also ships with Compiz, which can draw your wallpapers instead of Nautilus if you tell it to, and Compiz supports different wallpapers on different workspaces. Compiz, unfortunately, does not support managing icons on the desktop, only the wallpapers.

BUT I think Screenlets can be run particular to each desktop. If you're really intent on it, you could use Compiz for the wallpapers and Screenlets instead of desktop icons. This will be more taxing on your CPU, so if you're on a netbook or something you might want to avoid it.

If you want to give it a shot, install the extra Compiz plugins, and set up the different wallpapers with the Wallpapers plugin. They won't appear until you disable Nautilus drawing the desktop; you can do this by running gconf-editor (type "gconf-editor" in a terminal) and unchecking apps/nautilus/preferences/show_desktop. Then install Screenlets and mess around.

As a side note, KDE (Kubuntu) supports different content on different desktops, but it's a bit more complicated to get the hang of.

---

### Post by llelectronics on 2010-11-14
Windowmaker can have different docks on different desktops. 
Perhaps this is something for you. (looking at the thread title which says lubuntu and windowmaker is a very lightweigtht windowmanager)
Lubuntu and LXDE don't support this. But you can test windowmaker out with lxde by simply edit the windowmanager in the session editor of lxde.

---

