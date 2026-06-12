---
title: "video driver help"
date: 2007-09-08
forum: Desktop Environments
---

### Post by jaggedseven on 2007-09-08
i am new to the world of linux and i am having a hard time finding drivers for my system, i am using an intel mobo running the Intel GMA X3000 Onboard Video Chipset and i can't find a good river for it. anyone got any help for me? i have been on google for 3 days looking and got notting.

if this helps here is the [mobo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121052")

---

### Post by tyggna1 on 2007-09-08
try the opengl driver.  It works well with intel and Nvidia graphics cards.

For all the specifics on it, go to the terminal and type in 
```
man opengl
```
or whatever the specific name of that driver is.  That'll give you all the options for tweaking it.  If it doesn't work, just make sure that you backup xorg.conf before changing anything, so you can easily restore it from the command line.

You may just have to experiment to find the right driver.  If you want to know how to do any of that,  check out [my zine]("http://ubuntuforums.org/showthread.php?t=542431") to learn how to test and fiddle with video cards.  It's under Video Drivers--driving games.

---

### Post by jaggedseven on 2007-09-08
thanks alot of the fast reply and all the help

---

