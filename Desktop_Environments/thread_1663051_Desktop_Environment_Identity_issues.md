---
title: "Desktop Environment Identity issues"
date: 2011-01-09
forum: Desktop Environments
---

### Post by markitzero on 2011-01-09
Hi, i've been a casual user of Xubuntu 10.10 (dual boot with XP) for a couple of months. I'd put off installing any updates for it and my problems have only arisen after I had some spare time and installed them.
Originally I had 3 options at Grub, Xubuntu, Safe Mode and Windows. After the update I had 5 options, _Ubuntu_, Safe Mode, Ubuntu again, Safe mode again and windows. The duplicates of Ubuntu and safe mode do the same thing and it logs me into XFCE, not Gnome.
Also the slick splash screen and shutdown which used to display Xubuntu is now displaying Ubuntu which displays startup processes such as battery checks which I do not need to know.
It still works fine, its just bothering me what's going on. I'd like it back the way it was if possible.

---

### Post by ajgreeny on 2011-01-09
The new instances of ubuntu stem from a new kernel in the updates.  It is absolutely normal and not something to concern yourself about.

I, like most users, always keep one "spare" kernel in case anything goes wrong with the one normally booted to.

Ignore it at the moment; when you get yet another kernel update and there are six in the menu, just uninstall the oldest, lowest numbered version using synaptic or software centre, but make sure the new one is OK first.

---

### Post by Krytarik on 2011-01-09
Regarding the missing splash screen, check in "/boot/grub/grub.cfg" if there is the "splash" option at the end of each *normal* linux kernel line.

If it's not, open "/etc/default/grub" for editing, in a terminal:
```
sudo gedit /etc/default/grub
```and add that option at the end of the entry "GRUB_CMDLINE_LINUX_DEFAULT", like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```then save it and do
```
sudo update-grub
```
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

Greetings.

---

### Post by markitzero on 2011-01-10
Cheers guys :)

---

