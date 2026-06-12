---
title: "How to make new desktop icons appear on the primary monitor by default"
date: 2024-05-23
forum: Desktop Environments
---

### Post by goodstuff9 on 2024-05-23
ubuntu 22.04.4, gnome 42.9, Wayland


In the Ubuntu/gnome settings, I have five monitors, monitor #1 is set as the primary monitor.  Also in settings, I have enabled that new icons should be placed on the desktop in the top right corner.  


I have verified that in ~/.config/monitors.xml that monitor #1 is set as primary.  


I have verified that /var/lib/gdm3/.config/monitors.xml exactly matches what is in ~/.config/monitors.xml, and that the ownership of the /var/lib/gdm3/.config/monitors.xml file is gdm:gdm.  


Whenever I create a new item to be saved on the desktop, it goes in the top right corner of monitor #2.  How do I make it go in the top right corner of monitor #1?

---

