---
title: "Too Many Desktops"
date: 2008-03-06
forum: Desktop Environments
---

### Post by pyrocajun2707 on 2008-03-06
This is a question about a problem I'm having with PCLinuxOS 2007. I know this is an Ubuntu forum; I use Ubuntu for my own purposes, but this computer is for my Mom, who is a total noob when it comes to computers in general, much less the open-source world. I found that PCLinuxOS would be better for her because of its Windows-like implementation of KDE.

Anyway, I just enabled Compiz-Fusion, and for some reason, every time I start X, the taskbar shows 16 desktops enabled. The 3D cube works fine and everything, but it's just annoying having 16 desktop buttons on the taskbar. Every time I restart X, they comes back, even when I right-click the desktop buttons and set them to the preferred 4 desktops. Funny thing is, the KDE control module for configuring the desktops shows that there are 4 desktops when 16 are active, and to set it so there are 4 active, I have to set the configurator to 1 desktop. I've even had this problem with the new "Mini-Me" 2008 edition. 

If there's anyone around here who knows how to permanently fix this issue, or even anybody who knows what I'm talking about, please help me out, here. My beloved PCLOS has never been this stubborn with me before, and I would like to know that it hasn't failed me.


In case you must know, the system specs are:

AMD Athlon X2 6000+
HIS Special Edition Gfx card w/512mB DDR3 and factory-overclocked ATI x1950 GPU
                        (Personally-Installed ATI's Binary Driver and Catalyst Control Center)
4GB OCZ Gold 800mhz DDR2 RAM
Gigabyte GA-M61P-S3 motherboard w/ nForce 430 chipset (Max. 16GB RAM :D )

---

### Post by mcduck on 2008-03-06
You have to set the number of desktops in Compiz settings.. What you are now seeing is that KDE makes 4 desktops, and then Compiz turns each one of them into a cube with 4 desktops, so you get 4x4=16 desktops..

Set KDe to 1 desktop and then Compiz to whatever number of desktops you want, and the problem will be gone..

---

### Post by pyrocajun2707 on 2008-03-06
Oh, lord. I do feel like the idiot now.

Thank you very much, my friend. I appreciate your assistance.

---

