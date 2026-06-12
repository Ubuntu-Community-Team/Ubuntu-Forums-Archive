---
title: "Can I &quot;retore&quot; back to origonal state, and other questions"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by rBGH on 2007-12-16
I have two questions

First, is it possible for me to restore Gusty Gibson back to it's original state without loosing all the data that is stored in my email and IM programs. Numerous failed attempts to install Beryl and Compiz have left my machine with a longer that desirable loading time. 

Once done, I would like to know how to install the very cool feature that is "the cube". I've installed Compiz, Advanced Desktop effects setting, and Emerald but to no avail. 

I recognize the fact that it may be the effects themselves that are taking so long to load but I would still like to know how to do a restore. I have run code I didn't understand and installed BS that didn't work and I feel I have "soiled" my machine in the process. I'm only sort of joking here. 

I am new to Linux as of last June's article in Maximum PC. I like it so far and have a duel boot with Windotes on the raid array. 

My rig is
AMD Athlon Barton core 2500 OC to a 3200
Asus A7N8X-E Delux mobo
1 gig Kinston ram
Saphire 9800 pro AGP 8X
**Currently with the restricted driver From ATI **
2X 120WD SATA in a raid 0
2x 160WD IDE

When it comes time, I'll start in a another thread (unless someone wants to answer these questions now) about how to move my home folder to a different partition, ask how to start programs from the windotes equivalent of the launch icon, and where the information is stored for Evolution email so I can keep a back up of all that personal data  so I can restore it when ever I do a fresh install. 

Thanks for any and all help. I do appreciate it.

---

### Post by Ub1476 on 2007-12-16
I don't know if there're any apps which will "restore" Ubuntu for you, but you can reinstall and just backup /home.

For Visual Effects, this comes preinstalled in Ubuntu 710, Gutsy Gibbon. I suppose your graphic card is ATI Radeon 9800, but to be sure post the result of:

```
lspci | grep VGA
```

According to a quick Google search this should work with the open xorg drivers.

---

### Post by rBGH on 2007-12-16
> **Ub1476 said:**
> I don't know if there're any apps which will "restore" Ubuntu for you, but you can reinstall and just backup /home.

For Visual Effects, this comes preinstalled in Ubuntu 710, Gutsy Gibbon. I suppose your graphic card is ATI Radeon 9800, but to be sure post the result of:

```
lspci | grep VGA
```

According to a quick Google search this should work with the open xorg drivers.

boss@boss-desktop:~$ lspci | grep VGA
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
boss@boss-desktop:~$

---

### Post by Ub1476 on 2007-12-16
Here's a quick quote which should fix your driver:

> **Deadl0ck said:**
> OK - Got it sorted.

Here's what I did for anybody interested :

Run the Excellent "Envy" tool available here:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This set up the graphics card correctly, however, everything was still jumpy.
To fix it I had change my Colour depth from 24-Bit to 16-Bit. (I did this my manually editing my xorg.conf, and then rebooting)

All was good after that :D

---

### Post by rBGH on 2007-12-16
> **Ub1476 said:**
> Here's a quick quote which should fix your driver:

I read the Envy title page and it sounded good so I downloaded the installer, but when I ran it, I got this,

Only one software management tool is allowed to run at the same time
Please close the other application e.g. 'updated manager,'aptitude' or 'Synaptic' first.

The when I try to run Synaptic Packet Manager, I get this,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Oh, would this be the restricted drive manager? wait
I can't uninstall it because I can't open SPM,

This happened after I ran some code,

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

---

### Post by Ub1476 on 2007-12-16
Run this in the terminal:

```
sudo dpkg --configure -a
```
Now logout and login and run Envy.

---

### Post by rBGH on 2007-12-16
> **Ub1476 said:**
> Run this in the terminal:

```
sudo dpkg --configure -a
```
Now logout and login and run Envy.

The command you gave me unlocked everything and Envy installed like clock work.
Thank you very much. 

I get the same type of effect as I was before the install.  It's as if I have the cube but only have two desk tops so it's a flat cube. It flips when I use my scroll wheel.

---

### Post by Ub1476 on 2007-12-16
That is because you currently only have to Desktops (virtual). You'll need the Compiz configurator, also called Advanced Desktop Effects. It's in add/remove.

When it's installed, open System>Preferences>Advanced Desktop Effects>General Options>Desktop size>Horizontal>4.

Remember to set Visual Effects to custom as well.

Have fun exploring Compiz-Fusion:)

---

### Post by rBGH on 2007-12-16
> **Ub1476 said:**
> That is because you currently only have to Desktops (virtual). You'll need the Compiz configurator, also called Advanced Desktop Effects. It's in add/remove.

When it's installed, open System>Preferences>Advanced Desktop Effects>General Options>Desktop size>Horizontal>4.

Remember to set Visual Effects to custom as well.

Have fun exploring Compiz-Fusion:)

Thank you very much for that wonderful little tid bit. Although it's not the three dimensional cube yet, I know that it's only a matter of settings to acquire it.

---

### Post by rBGH on 2007-12-28
An update.
After I reinstalled Gusty I was having problem again with my display settings. Just basic refresh rates and resolution issues. I installed Envy again and ran the configuration program like last time, only this time, I had the option to use the latest ATI driver. I don't know why it only just now came to me but it has been the solution to one big problem I was having. 

So, way to go on the Envy advice. I consider this matter closed.



I have others though so I'm sticking around for a while. Issues I mean. Yes, I have issues.

---

