---
title: "Gnome Background Properties won't start anymore"
date: 2005-02-04
forum: Desktop Environments
---

### Post by Kokosnuss on 2005-02-04
Hi, I've got a nasty little problem:
Since I added an additional background to the background properties, I can't start this program anymore. Deleting the the .svg file that I added didn't help.

Is there a file where all the background settings are saved that I could modify? Or do you have other ideas?

Thanks in advance,
Felix Feustel

---

### Post by ilari on 2005-02-04
[QUOTE=Kokosnuss]Hi, I've got a nasty little problem:
Since I added an additional background to the background properties, I can't start this program anymore. Deleting the the .svg file that I added didn't help.

Is there a file where all the background settings are saved that I could modify? Or do you have other ideas?

Thanks in advance,
Felix Feustel[/QUOTE]
 The available background images are listed in the file ~/.gnome2/backgrounds.xml. The current background image is configured as a gconf-key desktop/gnome/background/picture_filename.

---

### Post by zAo on 2005-02-04
[QUOTE=ilari]The available background images are listed in the file ~/.gnome2/backgrounds.xml. The current background image is configured as a gconf-key desktop/gnome/background/picture_filename.[/QUOTE]
Didnt you update Gnome? Restart X and voila.

---

