---
title: "Removing XFCE"
date: 2012-10-10
forum: Desktop Environments
---

### Post by SuperFreak on 2012-10-10
Running 12.04 with Cinnamon as my DE and I wanted to remove XFCE. I used the following command:
```
sudo apt-get remove xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4 xfwm4-themes xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers
```
XFCE appears to be removed (no longer choice in login menu) but the Blue Xubuntu screen comes up on boot up. Is it possible to get rid of that?

---

### Post by 2F4U on 2012-10-11
You would need to change the theming of the bootloader Grub:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by pqwoerituytrueiwoq on 2012-10-11
that is the plymouth theme

open [synaptic](apt:synaptic) and search for "plymouth-theme-" there are about ~20 themes
to change what one you are using run this (the above is to get more themes)
```
sudo update-alternatives --config default.plymouth
```

---

### Post by SuperFreak on 2012-10-11
@pqwoerituytrueiwoq  Thanks that worked perfertly

---

