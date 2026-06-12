---
title: "keyboard-configuration settings are not saved"
date: 2018-06-20
forum: Desktop Environments
---

### Post by Amunhateb on 2018-06-20
I have two layouts and want to use only one combo for switching(win+space). I tried to set it in /etc/default/keyboard adding grp:win_space_toggle with no luck. It seems like Gnome somehow sets this alt shift combo.. Because when I disable it with dpkg-reconfigure keyboard-configuration it comes back after reboot or sleep.

Ubuntu 18.04 x64

---

### Post by Amunhateb on 2018-06-20
finally found where to change that "alternative switch combo". Need to use gnome-tweak-tool and go to **Keyboard and mouse > Additional layout options > switching to another layout**

---

