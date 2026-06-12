---
title: "text login"
date: 2009-03-03
forum: Desktop Environments
---

### Post by harkness on 2009-03-03
hi
i've just recently installed kubuntu and downloaded and installed the ati proprietary driver, its defaulted to a resolution higher than my monitor, so i can't view x, how can i get it to boot to a text login where i can run the ati config file and set my resolution? always worked fine with opensuse using the distribution specific package, but there wasn't an option for kubuntu

cheers

---

### Post by celticbhoy on 2009-03-03
Boot into recovery mode, and there is an option to setup screen resolution.

---

### Post by harkness on 2009-03-04
i have booted in to recovery mode, there is no option to change resolution, just one to try fix the x server, it doesn't work. initially on my monitor which is a 19" tft it was saying 1600*1200 out of range, i usually use the monitor at 1280*960, i then tried to connect it to my tv through hdmi from dvi, which technically won't display 1600*1200 either but tends to just try show an image, on that it displayed my login screen but totally messed up, i could make out enough to log in and try change my screen settings in kde, but x crashed before i could, probably, due to this driver. now when i connect to the monitor again i'm just getting kubuntu loading screen at first, then when my login screem should come up i get what looks like purple scribbles, presumably from a messed up x server. if i press CTRL + ALT + F* and get a text login prompt and login, i have tried running the aticonfig-iniitial, but the computer just crashes before i have much of a chance to do anything and the monitor turns off presumably due to x crashing in the background, any ideas?

---

### Post by harkness on 2009-03-04
ive just decided to cut my losses and install kubuntu again, i think where i messed up was by restarting x before running the aticonfig file, i have now done that, and set my resolutions using aticonfig --resolutions= or whatever it was. now in kde i've got 1280*960, the resolution i was looking for, working on the ati drivers, but the screen is going black for a few seconds a few times per minute, i'm wondering if it could be anything to do with the refresh rate but i don't know how to change it, also its calling my monitor crt1, its a tft screen, i don't know if thats going to make any difference or if crt1 is just what its calling the dvi output on my card (X1650XT), any help is massively appreciated

---

### Post by celticbhoy on 2009-03-04
As you are now into a desktop (of sorts) you could try and re-install the graphics driver.

---

