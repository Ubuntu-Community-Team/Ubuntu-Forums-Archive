---
title: "[SOLVED] Compiz Fusion"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by Znort_Ubern00b on 2007-11-08
Hi all,

I'm running Feisty with nvidia 128mb 2500 apg 8x graphics card. have installed compiz fusion and am now lost as to how to get settings to work.I don't get a cube when i set that as option...its is just a single sheet with two sides.

Also when compiz is running i do not get the page border with the min,max and close buttons.(did get this in beryl as well when i ran that)

Has anyone else had this problem?Or does anyone know why i get these probs?Any help would be tgreat.

---

### Post by Redenbacher on 2007-11-08
If you are running Fiesty, you need to go to System -> Preferences -> Appearance -> Visual Effects -> Advanced options. There you'll see a menu of enabling/disabling different plugins, one of which is the cube. Enable it, and you should have a cube! 

There actually might be an easier way to get to that option menu right in the preferences menu, but I'm not on my ubuntu box at the moment.

As far as window borders, install Emerald Theme Manager from Synaptic, press Alt+F2, and enter "emerald --replace"


Hope this helps!

---

### Post by Forlong on 2007-11-08
> **Znort_Ubern00b said:**
> I'm running Feisty with nvidia 128mb 2500 apg 8x graphics card. have installed compiz fusion and am now lost as to how to get settings to work.I don't get a cube when i set that as option...its is just a single sheet with two sides.
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Getting the cube".
> **Znort_Ubern00b said:**
> Also when compiz is running i do not get the page border with the min,max and close buttons.(did get this in beryl as well when i ran that)
Try this in a terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
(then restart X and see if it worked)

---

### Post by LEDZO on 2007-11-09
I am having the same problem but with gutsy.
 when i got appearance and try to turn on effects, it closes all windows then brings them all back up and displays the error that desktop effects could not be enabled

edit* i have an ati graphics card and i saw something about getting xgl but i dont know what it is.

---

### Post by Forlong on 2007-11-09
What card exactly? You *may* not need Xgl.

---

