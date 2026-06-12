---
title: "llvmpipe how to use it?"
date: 2013-09-04
forum: Desktop Environments
---

### Post by jhay2 on 2013-09-04
Hello There, 

I heard that theres a graphics driver that can enable 3D rendering even if your device is not supported ? and that driver is llvmpipe if im not mistaken , 

im interested with this driver , i already installed it using apt-get install llvm-dev.. 
but i dont know if it is already working ,

when i tried checking glxinfo | grep renderer , it seems that it is not running . 

how can i enable this driver ? should i install unity or gnome first? or it can be enable without installing one of this windows manager.. 

By the way im using ubuntu 13.04 server running lxde-core as windows manager.. 


if unity or gnome is needed before llvmpipe will enable ? 

how can i install unity ? 

i already tried sudo apt-get install unity
and install it , but when i try to use unity . it is not available in desktop choices ? 


sorry for my bad english .. 

Thank you :)

---

### Post by grahammechanical on 2013-09-04
1) llvmpipe is part of the Nouveau open source video driver. Install Nouveau and get llvmpipe. I think that you have installed a development library.

2) There is only one Ubuntu desktop and that uses Compiz+Unity. You need to install Ubuntu-desktop. That will bring in Compiz and Unity, which is a Compiz plugin, as well as Lightdm which is the login screen manager. Selecting Ubuntu as the desktop will give you Unity.

3) Running on llvmpipe. Select Recovery Mode>Resume at the Grub menu will get us running Unity on llvmpipe, even if we are using a proprietary video driver.

If the graphic adapter is capable of running Unity 3D on Nouveau then llvmpipe will not be activated. If the graphic adapter is not capable of running Unity 3D then llvmpipe will automatically be activated and run a fair approximation of Unity 3D.

I know of no way to "switch" one video driver off and another on except by activating one and deactivating the other in the process. 

Regards.

---

### Post by jhay2 on 2013-09-04
Thanks for your reply sir
Nouveau? 
How can i install Nouveau?

=>so it means that installing Ubuntu desktop ,llvmpipe will automatically activated? 


Sorry for asking too many . Im very new in Linux ,



thank you

---

### Post by jhay2 on 2013-09-06
This is not yet solved :(



i already did fresh install of ubuntu desktop 13.04 but unity still not work.. theres a login display but no desktop display .. :(

so i'd install gnome-shell and panel.. now im using gnome windows manager.. 

i already install libg3dvl-mesa 
and reboot but llvmpipe is not enabled ..

---

