---
title: "Can't remove desktop icons in Unity. Gconf doesn't work."
date: 2011-10-29
forum: Desktop Environments
---

### Post by Pisandelli on 2011-10-29
Guys, I was using Gnome 2 and AWN. I have a custom desktop with icons and configurated them trough Gconf-editor (and after, using ubuntu tweak). When I upgraded to Ubuntu 11.04, I decided to give a chance to Unity, but I can't remove the desktop icons. In GConf-editor all the checkboxes are unmarked, and is the same thing in ubuntu tweak... but the icons are still there! I can't remove them throwing them into the trash... and the file in my .local and .gconf are configured with "false" to desktop icons...

---

### Post by Sonador on 2011-10-29
Hi, try **dconf-editor** instead, it is for gnome3 (and thus for unity). In the editor you might be interested in paths: org>gnome>desktop>background and org>gnome>nautilus>desktop.

---

### Post by Pisandelli on 2011-10-29
Thank you Sonador! I had to install dconf-tools (sudo apt-get install dconf-tools)... no problem... I found the options like you said! Everything is fine now! Thank you very much!

---

