---
title: "Strange Desktop/Mouse Problem"
date: 2010-08-19
forum: Desktop Environments
---

### Post by artium on 2010-08-19
I have the latest Ubuntu (Installed a month ago) and Logitech LX7 mouse.

Right after I log in everything is working fine. But if I open any GUI application the mouse stops working. I can still move it around the screen, but clicking produces no effect.
The keyboard still works. 



The following can be part of the problem. If I try to turn off the computer with the terminal command:
```
sudo shutdown 0
```The system freezes right near the end (the computer is still on) with the following log on the screen (last 5 lines):
[QUOTE=Ubuntu]
* Asking all remaining processes to terminate...
init: upstart-udev-bridge main process ended respawning
init: rsys main process ended respawning
init: arcron main process (1840) killed by TERM signal
init: disconnected from system bus
[/QUOTE]



Any suggestions would be appreciated.

---

### Post by kbless7 on 2010-08-19
Have you tried a different mouse to eliminate causes?

---

### Post by artium on 2010-08-20
The problem was solved (almost by itself).

I tried a different mouse as you suggested, the problem was gone.

After this I have inserted the original mouse back and now everything works fine.

---

