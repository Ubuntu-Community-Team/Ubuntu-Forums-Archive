---
title: "Changing keyboard layout system wide with gnome-shell"
date: 2013-05-08
forum: Desktop Environments
---

### Post by lviggiani on 2013-05-08
Hi,
I'm running Ubutnu 12.04.2 LTS with gnome shell (from gnome team ppa) and gdm (lightdm has been uninstalled).
When I installed my computer I had a swiss german keyboard that now is set as the default one.
On my account on gnome shell I have set the new keyboard (that in the mean time has been changed) to its correct new layout which is English (International with AltGr dead keys).
It work while in desktop environment, however in tty1 mode (ctrl+alt+f1) and on gdm login screen it uses the german layout instead.
Actually I don't see an option to apply settings system wide from gnome shell.
Is there a way to do so? If that has to be done manually changing config files, how do I find correct settings for layout English (international with...)?
Thanks!

PS: Ithe target computer is not connected to the internet.

---

### Post by dino99 on 2013-05-08
note: if you are using GS 3.8.1, only libgdm is used (gdm removed)
dconf (from dconf-tools) or gnome-tweak-tool might help

sudo dpkg-reconfigure locales

---

