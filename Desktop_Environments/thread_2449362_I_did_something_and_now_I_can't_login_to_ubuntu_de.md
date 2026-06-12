---
title: "I did something and now I can't login to ubuntu desktop (20.04)"
date: 2020-08-25
forum: Desktop Environments
---

### Post by kymnyth on 2020-08-25
I was using ubuntu desktop and then installed the mate desktop and switched to lightdm.  I decided I wanted to go back to ubuntu desktop so I uninstalled mate and switched back to gdm3.  Now I get the gdm login screen but when I login, i get  a grey screen, mouse cursor and a message that says: System tray is unavailable, don't close your window.  I don't have access to my desktop anymore and I don't want to reinstall.  Can someone help me fix this please?

---

### Post by ActionParsnip on 2020-08-25
If you press CTRL + ALT + T do you get a terminal? If so, you can reinstall the ubuntu-desktop package which may help

---

### Post by kymnyth on 2020-08-25
I finally figured out the problem and I am adding this here in case someone else needs the solution.  I was running synergy so I could run this system with the mouse and keyboard from another.  I started it from my .profile.  Something went wrong with synergy.  I uninstalled it and removed the entry from .profile and everything worked after that...   Unfortunately I uninstalled and reinstalled 2 or 3 desktop environments as well as X11 in the process to try and figure it out.

---

