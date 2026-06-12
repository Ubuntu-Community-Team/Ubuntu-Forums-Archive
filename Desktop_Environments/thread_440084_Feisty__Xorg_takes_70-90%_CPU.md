---
title: "Feisty : Xorg takes 70-90% CPU"
date: 2007-05-11
forum: Desktop Environments
---

### Post by wgandhi on 2007-05-11
All,

My system configuration for a 915 based system is as follows :
1 IDE drive
   Installed Kubuntu with Feisty
1 DVD slave drive on the same IDE connector
2 SATA drives :
   Installed Ubuntu with Feisty
   Installed XP PRO

The Kubuntu boot works great. Only issue is that HALD takes a long time to start, for now ok..

XP PRO works as well as it could...

Ubuntu is extremely sluggish. A listing of "top" shows that the Xorg is  taking anywhere from 70% to 90 % CPU. I am using the direct rendering capability. No compiz or any 3d desktop is enabled..

I am not sure where to start looking to find a probable source of error. I have a 22' monitor which seems to work fine in all other configurations. 
Any pointers for debugging this problem will be appreciated.

-Wishwesh

---

### Post by Praill on 2007-05-11
It would be better to let us know the amount of ram you have and the cpu speed.
As far as requiring system resources: KDE > Gnome > XFCE

If you are running 256mb or less system memory then XFCE (Xubuntu) is recommended. If this is not the case or you love KDE and wont do without it you could disable some of its windows effects. Im on a windows machine at work right now so I cant remember the exact process. Its probably something like right clicking on the bottom bar and selecting configure. You can turn off all sorts of things that will hog resources like window decoration, program bar previews, etc.

---

### Post by Praill on 2007-05-11
EDIT: Sorry I read your problem wrong. You say Kubuntu runs fine but Gnome doesnt? This is certainly strange.
Im dunno if I can be of any help here. I would suggest maybe recompiling X but I wouldnt know hwo to do this.

Sorry.. im useless :)

---

### Post by wgandhi on 2007-05-14
Interesting.. I updated the BIOS on the board I am currently using. That magically fixed the problem altogether. I have no idea why ubuntu was so much more different than kubuntu but am happy that the problem is gone and I am not able to enjoy feisty @ speed.

-Wishwesh

---

