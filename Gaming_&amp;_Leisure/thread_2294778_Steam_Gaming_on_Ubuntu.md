---
title: "Steam Gaming on Ubuntu"
date: 2015-09-13
forum: Gaming &amp; Leisure
---

### Post by user38 on 2015-09-13
Hi everyone!

New member here, fairly novice Linux user. Tried out several distros over the past 3-4 years.

I recently messed up my laptop and deleted my Windows 8 recovery partition (ya, I'm an idiot), not knowing a recovery USB drive was not enough to do a reinstall. No DVD drive to do a reinstall from ISO disc, and can't figure out how to install from USB. So now I'm a full install Ubuntu user...! Yeah! I guess it takes adversity to force change sometimes. In a way I'm happy to finally shake off Windows.

But, I have some problems.

Gaming.

Since I installed Ubuntu and Steam, downloaded/set up a few games, I've noticed performance is much lower than it was on Window 8. I'm getting very choppy frame rate and have to run at absolute lowest settings and resolution just to get playable performance.

Is there something I'm missing with drivers? I have an i7-3517u and Intel Graphics 4000 Asus Zenbook. 

Something I can do to boost performance back up? Kinda miss top fragging in CS:GO, if you know what I mean.

Any help is much appreciated, thanks! 

:p

---

### Post by Bucky Ball on 2015-09-13
*Thread moved to **Gaming & Leisure**.*

This is the place. ;)

Welcome. Are you using the open-source drivers or the proprietary ones? Open Additional Drivers and check if there is something available there (mention what it is before installing). 

Have you updated the machine since install? Good idea to do that now if you haven't then reboot. You can do it with Software Updater or via a terminal with:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

This will not upgrade your system to a newer Ubuntu release, just upgrade the software you have installed in the current one.

---

### Post by CitadelUniversal on 2015-09-13
What type of Asus Zenbook are you using? Is it this [https://www.asus.com/Notebooks/ASUS_ZENBOOK_UX32A](https://www.asus.com/Notebooks/ASUS_ZENBOOK_UX32A) - or something else and have you tried installing the intel native linux graphics card drivers from intel or in the additional drivers software? If its a performance issue try turning off vsync this could increase the fps/performance rate.....

---

