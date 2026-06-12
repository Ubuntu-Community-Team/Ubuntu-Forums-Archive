---
title: "Installed LXQt but can't choose it at login"
date: 2016-02-03
forum: Desktop Environments
---

### Post by Andrea_Nistic on 2016-02-03
Hi to everyone!
[COLOR=#111111][FONT=Ubuntu]I installed LXQt in Lubuntu 15.10 from lubuntu-daily ppa with
[/FONT][/COLOR]```
sudo apt-get install lxqt-metapackage lxqt-panel
```
[COLOR=#111111][FONT=Ubuntu]But when I reboot, in the circle-lubuntu-icon at the top right I can choose only between Lubuntu, Lubuntu-Netbook and Openbox. No LXQt traces. How can I start it?[/FONT][/COLOR]

---

### Post by BenB1 on 2016-06-30
> **andrea_nistic said:**
> hi to everyone!
[COLOR=#111111][FONT=ubuntu]i installed lxqt in lubuntu 15.10 from lubuntu-daily ppa with
[/FONT][/COLOR]```
sudo apt-get install lxqt-metapackage lxqt-panel
```
[COLOR=#111111][FONT=ubuntu]but when i reboot, in the circle-lubuntu-icon at the top right i can choose only between lubuntu, lubuntu-netbook and openbox. No lxqt traces. How can i start it?[/FONT][/COLOR]

bump!

It may be a person needs to set up some init code in their ~/.xinitrc such as ```
exec LXQt
```.  Not quite sure though as I think the display manager uses wayland instead of xserver.

---

### Post by vasa1 on 2016-07-01
> **BenB1 said:**
> ... Not quite sure though as I think the display manager uses wayland instead of xserver.Why do you think that :confused:

---

