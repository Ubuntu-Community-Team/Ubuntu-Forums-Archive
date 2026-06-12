---
title: "Random idle time out Ubuntu Mate 16.04"
date: 2018-04-18
forum: Desktop Environments
---

### Post by jeiydee on 2018-04-18
Hello there! Would like to seek some inputs with  regards to Mate's (Ubuntu 16.04.4 LTS) behavior of having random idle  time outs.
  
Problem: Observing idle timeout intervals of 10s, 20s, 30s, 40s  randomly. "Dim display when idle" is ticked in the Mate Power Management  Preferences.
  
Tshoot steps made:[INDENT]
Tried using "gsettings set  org.gnome.settings-daemon.plugins.power idle-dim-time 60" but  idle-dim-time is not initially listed from  org.gnome.settings-daemon.plugins.power.gschema.xml ([https://askubuntu.com/questions/98184/increase-screen-idle-dim-timeout](https://askubuntu.com/questions/98184/increase-screen-idle-dim-timeout))
Added idle-dim-time from the step above and initially applied 10s value but still getting random idle times
Edited via dconf editor GUI for newly added idle-dim-time but still has random idle times

[/INDENT]
All help would be highly appreciated!

---

