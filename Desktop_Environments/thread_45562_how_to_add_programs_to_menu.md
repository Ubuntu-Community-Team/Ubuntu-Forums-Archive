---
title: "how to add programs to menu"
date: 2005-06-30
forum: Desktop Environments
---

### Post by polloz on 2005-06-30
hello,

i just installed tuxracer, but the thing is the when i click on aplications and go to games, tux is not there. i refreshed the gnome panel, but still nothing. how do i add applications to the menu?
also, i installed the nvidia driver some days ago, with the nvidia settings application. it appeard in my system tools folder in the menu, but the thing is that it doesn't has an icon of its own, it has just a square. how do i set the icons i want for the applicaitons listed on the menu?
thanks,

polloz

---

### Post by Omnios on 2005-06-30
Get Smeg "menu" editor from synaptic. You may change the icons by right clicking properties. There are a few other tricks like getting menu from synaptic which will give you all the old menu format menus under a Debian entri though a lot of people dont like Debian showing up in there menue. There is also a terminal menue refresh command posted some where in the forums though I dont recall it off hand.

---

### Post by h4rdc0d3 on 2005-08-11
To solve your nvidia settings icon problem...

In Console:
```
wget http://www.kde-look.org/content/download.php?content=16221&id=1
tar -xzf 16221-nvlogos.tar.gz
sudo cp nvlogos/64x64/apps/nvidia-settings.png /usr/share/pixmaps
```
Then do this:
1. Applications > System Tools > Smeg Menu Editor
2. In Smeg: System Tools > NVIDIA Settings > Right Click > Properties
3. In NVIDIA Setting Properties: Click box next to "Icon:" and select /usr/share/pixmaps/nvidia-settings.png
4. Click OK
5. Close Smeg

Btw, I posted this here because I didn't see it anywhere else.

---

### Post by Muhammad on 2005-10-03
Much appriciation for the Nvidia icon. [img]http://ubuntuforums.org/images/icons/icon7.gif[/img]

---

