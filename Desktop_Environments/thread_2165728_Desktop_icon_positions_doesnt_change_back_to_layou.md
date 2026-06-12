---
title: "Desktop icon positions doesnt change back to layout when switching between resolution"
date: 2013-08-06
forum: Desktop Environments
---

### Post by distortion_2 on 2013-08-06
Hi,

sorry for my bad english, I try to explain what's the problem:
I'm running an Ubuntu 12.04.02 LTS with Gnome Shell 3.4.1. When I come to office, I plug in my laptop into a docking station, where a 24inch monitor is connected to. The laptops display is 15,4inch. Everytime i switch working between docking station and without, the desktop icons are disordered on the screen. I just want to figure out, how the information about the icon positions is stored. (Maybe I could then start a script at system startup, which will reorganize the icon positions depending on the resolution.) I saw several workarounds on Google, but that seems just to be working for Gnome2. The Command:
```
gvfs-info metadata::nautilus-icon-position Firefox.Desktop
```
lists some information about the icon, but nothing useful referring to the position.

Any ideas? It's really annoying to reorganize the icons every morning :roll:

Thank you

---

