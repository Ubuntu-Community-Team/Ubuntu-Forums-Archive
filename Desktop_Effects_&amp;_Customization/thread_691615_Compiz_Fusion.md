---
title: "Compiz Fusion"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by ploik on 2008-02-08
Hi, i recently installed compiz fusion. i first encountered an error with an nvidia-glx, but after much hard work, i figured out how to fix it. then i searched the internet and found compiz fusion, and so far, it SEEMS that i installed it correctly, but when i click the "preferences" button, it does nothing, and when i click on the "custom" in the appearence screen, it says "Desktop effects could not be enabled." What is it that i might be doing wrong? i enabled the nvidia-glx, so 3d environment is enabled. also if there is an easier way of installing (without all the terminal stuff) please post a link, just to confirm that i installed it correctly.

---

### Post by overdrank on 2008-02-08
> **ploik said:**
> Hi, i recently installed compiz fusion. i first encountered an error with an nvidia-glx, but after much hard work, i figured out how to fix it. then i searched the internet and found compiz fusion, and so far, it SEEMS that i installed it correctly, but when i click the "preferences" button, it does nothing, and when i click on the "custom" in the appearence screen, it says "Desktop effects could not be enabled." What is it that i might be doing wrong? i enabled the nvidia-glx, so 3d environment is enabled. also if there is an easier way of installing (without all the terminal stuff) please post a link, just to confirm that i installed it correctly.

HI and if I may ask what is the model of the graphics card and version of Ubuntu you are using?

---

### Post by ploik on 2008-02-08
im using an Nvidia GeForce2 MX/MX400 and my ubuntu is 7.10 Gutsy Gibbon.

---

### Post by jnylen on 2008-02-09
> **ploik said:**
> Hi, i recently installed compiz fusion. i first encountered an error with an nvidia-glx, but after much hard work, i figured out how to fix it. then i searched the internet and found compiz fusion, and so far, it SEEMS that i installed it correctly, but when i click the "preferences" button, it does nothing, and when i click on the "custom" in the appearence screen, it says "Desktop effects could not be enabled." What is it that i might be doing wrong? i enabled the nvidia-glx, so 3d environment is enabled. also if there is an easier way of installing (without all the terminal stuff) please post a link, just to confirm that i installed it correctly.

If you installed Compiz Fusion using a custom procedure then Gutsy's Desktop Effects screen probably won't work.  Try running **compiz --replace &** from a terminal (this will replace metacity or whatever else as your window manager).  If that works, you can then add that command to your session preferences but without the &.

As for the settings, try installing the compizconfig-settings-manager package, then run the program ccsm.  See if you already have ccsm first.

I think everything that you did may have been unnecessary since Gutsy comes with some version of Compiz Fusion by default.  You could also try the following command:
**sudo apt-get install --reinstall compiz compizconfig-settings-manager**

---

### Post by ploik on 2008-02-20
Thanks, that worked for re-installing, and i can open the compiz settings and i get to turn on "desktop cube" and the other stuff. but the problem of actually enabling the desktop effects still remains. whenever i try to switch my effects to the "custom" option, or any option other than "none," it says "desktop effects could not be enabled." what can be wrong? the only thing i can think of is my "restricted driver" that i enabled, is that whats causing the problem? and if it is, how can i fix it? it is an NVIDIA accelerated graphics driver, just to let you know. any help at all will be appreciated. thanks in advance.

---

