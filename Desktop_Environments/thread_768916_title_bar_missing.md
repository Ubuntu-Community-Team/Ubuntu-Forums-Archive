---
title: "title bar missing"
date: 2008-04-26
forum: Desktop Environments
---

### Post by ps_kishore on 2008-04-26
title bar is missing. I installed compiz and uninstalled using synaptic manager. After restart title bar is missing for all windows. Any help is much appericated.

---

### Post by overdrank on 2008-04-26
> **ps_kishore said:**
> title bar is missing. I installed compiz and uninstalled using synaptic manager. After restart title bar is missing for all windows. Any help is much appericated.

Hi and have you tried ```
metacity --replace
``` using the alt, F2 keys.

---

### Post by hatman on 2008-04-28
> **overdrank said:**
> Hi and have you tried ```
metacity --replace
``` using the alt, F2 keys.

I had the same problem, removed the nVidia driver - took me a while to get it back up, still the same... ran the above and everythiong hunky-dory now... cheers...

---

### Post by bijeeshvs on 2008-04-28
hi buddy whats your problem is you messed up the window manager (the program that handles window border) metacity is the default window manager but as you have installed compiz Emerald is the best for you, u can open a terminal and type in
sudo apt-get install emerald
for installation after installation press Alt+F2 and type in emerald --replace also check in the settings of compiz that window decoration plugin is enabled
if the title bar disappears after reboot go to the sessions manager in settings and add a new startup program in the command box type in emerald --replace and save 

pls write back if this was helpful

---

### Post by shinkaide on 2008-04-29
> **hatman said:**
> I had the same problem, removed the nVidia driver - took me a while to get it back up, still the same... ran the above and everythiong hunky-dory now... cheers...

I did the same, but It looks like all it did was disable desktop effects. When I enable desktop effects again, it disappears again. SO basically, if you do it this way, the solution for the disappearing titlebar when desktop effects is to... deactivate desktop effects...

What can we do to have both?

> **bijeeshvs said:**
> hi buddy whats your problem is you messed up the window manager (the program that handles window border) metacity is the default window manager but as you have installed compiz Emerald is the best for you, u can open a terminal and type in
sudo apt-get install emerald
for installation after installation press Alt+F2 and type in emerald --replace also check in the settings of compiz that window decoration plugin is enabled
if the title bar disappears after reboot go to the sessions manager in settings and add a new startup program in the command box type in emerald --replace and save 

pls write back if this was helpful

I tried this, nothing happened.

---

### Post by bijeeshvs on 2008-05-01
Actually i dont know about your display drivers status, if you have not enabled the restricted drivers for your display pls enable them and here is a detailed guide about the installation and configuration of everything you need to enable the Desktop effects, follow it and i am pretty sure you will fix it. best of luck

dont worry we can fix it............................


[http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

---

### Post by lildunn34 on 2008-05-01
Im having these same issues as well. I first had an issue with getting advance desktop effects enabled and solved this by manually installing ATI1950 drivers.

---

