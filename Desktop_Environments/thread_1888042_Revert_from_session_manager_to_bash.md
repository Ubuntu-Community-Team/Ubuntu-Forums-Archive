---
title: "Revert from session manager to bash"
date: 2011-11-28
forum: Desktop Environments
---

### Post by Ra'anan on 2011-11-28
hey, so i've tried gdm/lightdm/kdm etc...

i'd prefer to revert to ubuntu 11.10 starting bash without the session managers,

i'm currently using xfce, xfwm and gdm but i'd like to properly remove gdm and just start a bash script at boot so i can go ahead and run startx when I want,

i'm a little weary of simply removing gdm and giving it a go, is there anything I need to do prior to removing gdm to get this working?

---

### Post by papibe on 2011-12-05
Hi Ra'anan.

Without uninstalling anything change the grub config as follows:

Edit your grub file:
```
sudo nano /etc/default/grub
```

Locate these lines:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
Change them to:
```
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
Save the file. Then update grub:
```
sudo update-grub
```
Then restart:
```
sudo reboot
```
Hope it helps, and tell us how it goes.
Regards.

---

