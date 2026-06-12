---
title: "Lost GNOME. How to restore?"
date: 2010-04-21
forum: Desktop Environments
---

### Post by spb1941 on 2010-04-21
Folks, here is this newbie's BIG PROBLEM. I placed the same issue on the "General" forum yesterday, but got no useful feedback or recommendations.

Somehow I managed to delete by mistake all Gnome palettes from my desktop (Ubuntu 9.10). All the desktop settings disappeared. Currently I can see only folders left on the desktop but couldn't launch any applications fron the GUI.

Can open console [CTRL+ALT+F2]and run line commands.

Any advise how to recover GNOME and rebuild my desktop configuration is appreciated. 

Thanks!

---

### Post by thomasaaron on 2010-04-21
Try going into recovery mode, and then selecting the netroot option. Make sure you have a wired internet connection before doing so. Then run this command...

apt-get --re-install install ubuntu-desktop

---

