---
title: "&quot;Desktop effects could not be enabled&quot;"
date: 2010-04-12
forum: Desktop Environments
---

### Post by kshawkeye on 2010-04-12
Two days ago my desktop effects worked without a problem, now, today, for some odd reason they chose to not work. 

Anyone know the cause? 

I'm running Ubuntu 9.10 with an ATI Radeon 9250 graphics card with 2 gigs of ram and a 2.8 GHz processor. 

I haven't change a thing relating to graphics, and I have no clue why this would happen two days after a fresh install of Ubuntu.

Also, two days ago my native resolution (1680x1050) wouldn't display my background or icons, now it seems to work. So I lose desktop effects, but gained a working background. Anyone have any ideas?

---

### Post by kshawkeye on 2010-04-16
Anyone?

---

### Post by Jguy on 2010-04-16
Have you updated your system recently? I've found that if you haven't installed the ATi drivers via the "Restricted Hardware" tool, then if you update your system (either kernel or with some driver updates), Xorg seems to crap itself and not like desktop effects. Try reinstalling your video card drivers via "Restricted drivers" (uninstall the old one and go to System -> Administration -> Hardware drivers and install the open source one).

---

### Post by kshawkeye on 2010-04-16
[quote=Jguy]Have you updated your system recently?[/quote]

Yes, I guess I have. I installed a fresh copy of ubuntu and then it forced me to updated and in that update I believe it updated my system.

[quote=Jguy] Try reinstalling your video card drivers via "Restricted drivers"  (uninstall the old one and go to System -> Administration ->  Hardware drivers and install the open source one).[/quote]

When opening System -> Administration -> Hardware Drivers, Hardware Drivers says "No proprietary drivers are in use on this system." So I am unable to uninstall or reinstall any drivers.

---

### Post by shaka_zulu on 2010-04-16
Search the forum on how to uninstall Ati drivers. After you do that reboot your system and try again to install them from hardware drivers because your video card should be recognized.

---

### Post by clemm on 2010-04-16
I have the same problem. After an update to a newer version, my screen is blank. All black, no icons, and I have wallpaper selected but it will not show it. I do not think this is a driver problem. When I log off or shut down it briefly displays the screen like its supposed to be ???

---

