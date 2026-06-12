---
title: "Notebook hotkeys not working in KDE"
date: 2006-06-17
forum: Desktop Environments
---

### Post by zaiyon on 2006-06-17
Hi, I'm using ubuntu on a Dell Inspiron 1300 notebook.

The volume up/down etc. hotkeys worked fine out of the box, I think this is thanks to the hotkey-setup service.

But only in Gnome, I have none of these hotkeys in KDE or XFCE4.

I installed kubuntu-desktop and xubuntu-desktop, so I'm wondering what I'm lacking. Any ideas what to do about this?

---

### Post by njf on 2006-06-17
See [https://wiki.kubuntu.org/KubuntuVolumeHotkeys](https://wiki.kubuntu.org/KubuntuVolumeHotkeys)

IIRC you need to put a shell script with "xmodmap ~/.xmodmaprc" in ~/.kde/Autostart/ .

---

### Post by zaiyon on 2006-06-17
I do not have a xmodmaprc, since I didn't set a single thing up about this myself. All worked out of the box for gnome, and now I have no clue how to have this functionallity in the other DEs.

---

