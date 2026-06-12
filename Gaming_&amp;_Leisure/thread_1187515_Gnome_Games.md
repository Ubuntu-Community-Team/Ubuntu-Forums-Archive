---
title: "Gnome Games"
date: 2009-06-14
forum: Gaming &amp; Leisure
---

### Post by Jion_Wansu on 2009-06-14
Anyone know how to reset the scores of Gnome Games, especially Gnometris 2.24.1.1

---

### Post by 73ckn797 on 2009-06-14
It is in Places/Computer/File System/var/games/gnometris.scores. It is a text file that you can delete the entries and save as an empty document.

You will probably need to open the terminal and enter:
```
gksudo gedit /var/games/gnometris.scores
```If you have installed "gksu" from the repos you can right click the file in the file browser and open as administrator and accomplish the same thing.

---

