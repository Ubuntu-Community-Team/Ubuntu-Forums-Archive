---
title: "Gnome menubar paths for fluxbox?"
date: 2009-05-04
forum: Desktop Environments
---

### Post by ilych on 2009-05-04
I find the Gnome menu bar on top (e.g., administration, preferences, places) useful. Where can I find the paths to the applications in the menu bar, so I can add them to my fluxbox right-click menu? When I automatically generate a fluxbox menu, it does not include the Gnome applications that are found in Gnome preferences for example.

---

### Post by Anzan on 2009-05-06
I would recommend that you install "menu", the Debian menu.

sudo apt-get install menu

You should be able to launch anyhting from that.

As for the paths to applications they will be in /usr/bin

You might want to put this in your menu:

   [exec] (Nautilus) { /usr/bin/dbus-launch nautilus --no-desktop }
   [exec] (GNOME Control) { /usr/bin/gnome-control-center }
   [exec] (Gconf) { /usr/bin/gconf-editor} 
   [exec] (Theme) { /usr/bin/gtk-chtheme }
   [exec] (Update) { /usr/bin/update-manager }

---

### Post by ilych on 2009-05-21
Great, thanks!

---

