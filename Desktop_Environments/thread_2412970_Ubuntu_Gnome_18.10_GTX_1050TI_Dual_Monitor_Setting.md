---
title: "Ubuntu Gnome 18.10 GTX 1050TI Dual Monitor Settings numbers reversed"
date: 2019-02-19
forum: Desktop Environments
---

### Post by jerry47 on 2019-02-19
I just replaced a GTX 650TI dual dvi gpu with a GTX 1050Ti with dvi, hdmi, display port. I just recently found out that gpu's scan ports after post in the following order dvi, hdmi, display port looking for a monitor. So in my case the left monitor is primary and dvi. The right is hdmi. In settings the left monitor is primary as number 2 and right is secondary as number 1. It works fine this way but one can't change to single display because the button is labeled number 1. Does anyone know how the monitors get identified and assigned the number because I want to id the left number 1 and right number 2? 

Thanks, Gerald

---

### Post by nicholasarussell on 2019-02-21
Hi Gerald,

Under screen display you are actually able to drag your monitors around like you would a desktop icon to the possition you need.

Give it a try and see if that helps :)

Also it could be driver related does it happen in the Open source drivers or the Nvidia ones? or both :)

Kind regards,

---

### Post by jerry47 on 2019-02-22
Thanks for the reply. The monitors are arranged in the proper order. The numbering is reversed from what it was before the GPU change. 

old GPU
Left monitor was #1 DVI-0 and right #2 DVI-1. Desktop on left. Single button always identified as #1 (no user choice for the number)

new GPU
Left monitor is #2 DVI-0 and right #1 HDMI-0. Desktop on left. The single display button on the right has only one choice for single display....#1.

So, if I go to single display the desktop moves over to the right. Because GPUs always scan like DVI-0 then HDMI-0 search for a connected display the left monitor displays the Asus splash screen after post. No drivers loaded at this point. 

I need to reverse the number assignments. If the monitors were identified by what they actually are DVI-0 and HDMI-0 and the single display button just went to the primary this would not be an issue. On the Nvidia GUI there is nothing about #1 or #2. The numbers have to be generated somewhere in the OS.

---

