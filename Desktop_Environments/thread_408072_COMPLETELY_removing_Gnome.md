---
title: "COMPLETELY removing Gnome"
date: 2007-04-12
forum: Desktop Environments
---

### Post by justin on 2007-04-12
How can I completely remove Gnome from Ubuntu Feisty. I have been using pekwm as a window manager for a while now, and have no need for Gnome anymore. I would like the computer to boot to a prompt, and not to the GDM. Any suggestions for a good, clean, and complete removal?

---

### Post by rsambuca on 2007-04-12
You might want to start with ```
sudo apt-get remove ubuntu-desktop
```, and then do a sudo apt-get autoremove.

---

### Post by hoheszeh on 2007-04-14
Depending on how excessive you 've 'customized' your system already, considering a server install + installing X, pekwm + the software you need, might be a way for a really fresh and reduced system.

---

