---
title: "Remove unity sidebar in 12.04"
date: 2012-08-15
forum: Desktop Environments
---

### Post by kerryhall on 2012-08-15
How do I remove the unity sidebar in 12.04?

*There is no "Ubuntu Classic" option on login
*Even if there was, I still want Compiz

Thanks!

---

### Post by wojox on 2012-08-15
[How to install classic gnome desktop in ubuntu 12.04 (Precise)]("http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html") easy enough. :P

---

### Post by vexorian on 2012-08-15
If you want to keep the global menu and dash, the "best" way is probably to make the sidebar (called launcher) hidden and make it so only a trigger on top left reveals it.

Else you can go gnome-classic, it can run compiz instead of metacity if you add this to startup apps:
compiz --replace

---

### Post by kerryhall on 2012-08-15
Sweet! 

sudo apt-get install gnome-panel 

did the trick.

I would like to note for anyone googling:

With a multimonitor/multi-monitor/multi monitor setup, unity is broken. The mouse warps to the wrong screen trying to move from monitor to monitor. The solution was to install gnome-panel, fixed the problem using gnome classic without effects.

Thanks for the help folks!

---

