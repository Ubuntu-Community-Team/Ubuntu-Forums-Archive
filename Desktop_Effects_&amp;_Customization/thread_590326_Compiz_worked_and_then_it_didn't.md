---
title: "Compiz worked and then it didn't"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by If I Get Old on 2007-10-24
I was running Feisty and running Compiz last week.  Using my older nVidia card I was never able to get the 3d effects but the effects I had were nice and I was able to run Avant. I also have been using the Compiz Fusion Icon to help switching things around quicker.

The update feature never did work so I have done a clean install of Gutsy.  I was able to get effects (3d and all) running with Gutsy until a system restart.  Before the restart Emerald only had the default red theme available.  Now when using Compiz I get no borders, there are no themes in Emerald, Avant will not work and my Screen Resolution Changes from 1280 x 1024 @ 60 hz to 1280 x 1024 @ 50 hz and I can't change it back.  

I have tried reinstalling Compiz and my drivers.  I don't have to have the cube but, it seemed to work for a day and I would love to have it.  Avant and Emerald really aren't deal makers but they make computing much more enjoyable.  Any help is greatly appreciated.

---

### Post by If I Get Old on 2007-10-24
I forgot to mention that while I can run Gnome I prefer KDE.  It previously worked in Gnome, KDE & xfce.

---

### Post by If I Get Old on 2007-10-24
I have now tried a fresh install again....I enabled the restricted driver and enabled desktop effects.  It worked temporarily.  I don't know what changed but now when I click on Extra in the Visual Effects tab I get "Desktop effects could not be enabled"

---

### Post by If I Get Old on 2007-10-25
bump

---

### Post by If I Get Old on 2007-10-25
Here is the terminal output for the following command

Compiz

```
john@dell-pc:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0201 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity]
```

---

