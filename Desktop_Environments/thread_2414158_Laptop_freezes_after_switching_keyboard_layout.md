---
title: "Laptop freezes after switching keyboard layout"
date: 2019-03-06
forum: Desktop Environments
---

### Post by foxy123 on 2019-03-06
I was trying to install Japanese keyboard layout in addition to three other layouts and messed up something after installing fcitx and trying to remove it. Now if I try to switch the layout, the laptop freezes completely and even after the reboot doesn't load Gnome (the screen stays plank after entering the login password). The only way to get into my account after that is to log into a separate account and there log in in the terminal like myself and execute:
```
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
```
Also if I tried to get into a different tty using say Ctrl+Alt+F3, it does not allow me to enter password. Basically I can enter a username but after that I see on the screen something like "Wrong password was entered" three time like it was being entered automatically.

---

