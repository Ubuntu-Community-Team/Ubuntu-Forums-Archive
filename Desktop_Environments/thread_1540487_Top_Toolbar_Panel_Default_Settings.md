---
title: "Top Toolbar Panel Default Settings?"
date: 2010-07-27
forum: Desktop Environments
---

### Post by jsells20 on 2010-07-27
I screwed up and deleted my top panel and I cannot figure out how to bring it back to the original default settings. After trying different things found in other posts like 

restart X, then in console:

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

now both top and bottom panels are gone. I need help to bring both panels back.
I'm on jaunty jackalope 9.04.

---

### Post by gtman on 2010-07-28
do this by your terminal

gconftool-2 --shutdown
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

your default panel will restored back...
fyi: i`m running lucid lynx

---

### Post by karmila on 2010-07-28
> **gtman said:**
> do this by your terminal

gconftool-2 --shutdown
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

your default panel will restored back...
fyi: i`m running lucid lynx

yes, this should be working.

---

