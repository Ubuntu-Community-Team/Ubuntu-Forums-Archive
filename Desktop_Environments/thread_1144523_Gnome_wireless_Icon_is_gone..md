---
title: "Gnome wireless Icon is gone."
date: 2009-04-30
forum: Desktop Environments
---

### Post by CodyK46 on 2009-04-30
And I can't figure out how to get it back on my panel. I can't connect to any wireless network.

---

### Post by pastalavista on 2009-04-30
You can launch Network Manager with the command```
nm-applet --sm-disable
```and you should add it to System > Preferrences > Startup Applications

---

### Post by dragonwarriorfan on 2009-04-30
Same issue here - when I tried the command, I got 

The program 'nm-applet' can be found in the following packages:
*network-manager gnome
*mythbuntu-diskless client
Try: sudo apt-get install <selected packages>
bash: nm-applet: command not found

EDIT: nevermind, just reinstalled.

---

### Post by CodyK46 on 2009-05-04
Other than my sleep/hibernate icon, sound, date/time and shutdown icons, everything else is gone. How do I get this back? It's not just wireless that is gone. My battery indicator, bluetooth, and torrent icon are gone.

---

### Post by pastalavista on 2009-05-04
Try right-ckicking the panel where it's supposed to be, select 'Add to panel' and add 'Notification Area'

---

