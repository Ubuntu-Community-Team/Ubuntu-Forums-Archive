---
title: "Gutsy Stole My Cube"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by Hmarroqu on 2007-10-05
Just started with Gutsy beta and the "desktop effects" is gone, my cube is gone but the wobble still works.  Can anyone tell Gutsy to give me my cube back? or show me how to?

---

### Post by adamorjames on 2007-10-05
[http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)
edit: look at the pics, it pretty much shows you the effects options. It will be the Extra (third) option. System -> Preferences -> Appearance

---

### Post by Hmarroqu on 2007-10-05
Yea that button for the "custom effects" that i believe says "preferences" does not appear, i figured that would be where to find my cube but i guess gutsy is hiding that button from me....

---

### Post by bikeboy on 2007-10-05
Install compiz-config-settings-manager

---

### Post by macogw on 2007-10-05
And install the fusion-icon to get the icon for quick access to configuration stuff.  Running CF from that (instead of from "enable desktop") makes it only run with the settings manager settings in effect.  The "Enable Desktop" had gconf settings overriding my ccsm settings and no cube.

You can get the fusion-icon from my PPA on Launchpad.  Add this to your sources.list
> 
deb     [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse
deb-src 
[http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse

and then 
```
apt-get install fusion-icon
```

---

### Post by adamorjames on 2007-10-05
Wow that link I gave you had half the answer and I didn't even know it -> "There's no cube (and that's particularly disappointing, since Feisty had an option to get it)." sry :)

---

### Post by Hmarroqu on 2007-10-05
Gutsy is pretty fancy...This is major eyecandy for a "stock" installation.

---

### Post by Forlong on 2007-10-05
Did you figure it out by now?

If not, see here: [How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) - there's a spefic section to get the cube working.

You have to install ccsm first:
```
sudo apt-get install compizconfig-settings-manager
```


The guide is not 100% up to date for Gutsy (but this will work) - I will update it in the next days.

---

### Post by DouglasAWh on 2007-10-20
> **Forlong said:**
> If not, see here: [How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) - there's a spefic section to get the cube working.

Getting the cube

Firstly, enable the following plugins (by checking the box next to them):

    * Desktop Cube - to actually use it, we might have to disable some other plugins (just follow the popup)

    * Rotate Cube - that is necessary to spin the cube


This does not work for me.  Both are checked and no dice.

---

### Post by virogenesis1 on 2007-10-21
> Firstly, enable the following plugins (by checking the box next to them):

* Desktop Cube - to actually use it, we might have to disable some other plugins (just follow the popup)

* Rotate Cube - that is necessary to spin the cube


This does not work for me. Both are checked and no dice.

I had exactly the same issue and I got my cube back by going to CCSM -> General Options -> Desktop Size and setting Number of Desktops = 1 and Horizontal Virtual Size = 4.

HTH :)

---

### Post by kubuntuuser on 2007-10-21
I was having the exact same problem. The tip about horizontal desktops fixed my problem.

Cheers

---

