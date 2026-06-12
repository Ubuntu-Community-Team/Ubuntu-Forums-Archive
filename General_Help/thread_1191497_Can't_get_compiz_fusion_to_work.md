---
title: "Can't get compiz fusion to work"
date: 2009-06-19
forum: General Help
---

### Post by This is Linux on 2009-06-19
I recently installed ubuntu 9.04 on a computer with a core i7 920, 6 gb of ram, and a radeon 4890. Obviously, this system should be fast enough for all the eye candy. However, I have no idea how to enable compiz fusion, and when I try to change the visual effects in appearance from basic to anything else, it says "the composite extension is not available." I am not sure what to do. One possible thing is that I am not using the default ati driver from the ubuntu repositories, but instead installed the 9.06 drivers from ati. I did this as, when I was using the default proprietary ubuntu driver, it gave me a watermark in the bottom right hand corner of the screen, saying "unsupported hardware." Also, I believe that this non-default driver is working properly, as I can use my monitor at 1900 x 1200, and when I ran glxgears, I got 10501.975 FPS. Can someone please help me get compiz fusion working?

---

### Post by mikewhatever on 2009-06-19
You need to install the proprietary driver. Check under System->Admin->Hardware Drivers.

---

### Post by This is Linux on 2009-06-19
I am sorry that I was unclear. I installed the proprietary driver, but not from the menu. I went to ati's website, downloaded the 9.06 linux drivers, and installed those. Should I uninstall those and go back to the ones provided by ubuntu, even though those give me the "unsupported hardware" watermark?

---

### Post by mikewhatever on 2009-06-19
Did you uninstall the driver provided by Ubuntu at any point? I think 9.6 should be better then 9.04's default, but you probably shouldn't have both.

---

### Post by delcypher on 2009-06-19
If you manage to get the proprietary driver working then you can install two useful tools for using compiz. Note everything in code is to be run on command line (Applications > Acessories > Terminal)

You can also test opengl support by using ```
glxgears
```

Fusion-icon:
Neat little system-tray icon that let's you choose your window-manager and window decorator.

```
sudo apt-get install fusion-icon
```

Simple Compizconfig settings manager:
Really nice control panel for compiz.

```
sudo apt-get install simple-ccsm
```

---

### Post by This is Linux on 2009-06-19
I did deactivate the default driver provided by Ubuntu, which I assume means that it is uninstalled. Is this assumption correct? Also, was able to run glxgears and I got over 10000 fps, does this mean that the driver is working? Do you guys have any other commands to figure out if the drivers are working?

---

### Post by This is Linux on 2009-06-25
I finally figured it out. I needed to enable the the composite extension in xorg.conf. ](*,) Oh well, and here are the posts that showed me if anyone else needs them - [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Mesa_drivers), [http://ubuntuforums.org/showpost.php?p=3530421&postcount=23](http://ubuntuforums.org/showpost.php?p=3530421&postcount=23), and this problem is finished, so mods can lock this

---

