---
title: "Weird squares and lines after icons."
date: 2014-05-09
forum: Desktop Environments
---

### Post by LukasLeon on 2014-05-09
Hello everyone, so i am using Ubuntu Studio, and i have upgraded from 13.10 to 14.04. Since this upgrade i am experiencing a very weird issue. Everytime i move some icon around a desktop, a weird blue squares and stripes remains there ( as seen on the picture, i couldnt take a screenshot, because when i hit prtscrn, the stripes just dissapear and desktop looks normal again ). I am using Compton as my window manager, i have tried to turn it off, but that didnt fix my issue. I have also tried different theme styles ( i am using "Greybird" most of the time ) but that didnt help neither. This is like the weirdest issue i have ever experienced on PC. I have no idea what can cause this, and it is really annoying.. Thanks for any advice..


[IMG]https://dl.dropboxusercontent.com/u/106919705/CAM00001.jpg[/IMG]

---

### Post by LukasLeon on 2014-05-11
Nobody knows how to fix this? :( It is really annoying.. maybe if i reinstall the XFCE? I am just not sure how to do that without screwing something up...

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-05-11
i don't know what is the solution to this problem but i recommend 'Synaptics Package Manager' to remove all about XFCE but before doing so install LXDE [Lightweight Environment] and see if such problem is there ? If so? then there's no good in re-installing desktop environment.

To remove Xfce completely without troubles, open Synaptic Package Manager and click Sections > Installed. In search box, type environment name eg 'Xfce' and all Xfce packages would appear. Select all of them > Mark for complete Removal (recommended) or Mark for Removal (which will leave packages .deb on you filesystem somewhere for future which is not good for re-installing as some bad package remain there and again cause problem)
and hit 'Apply'.
Wait for when it's done. . . Now an extra but useful step is to clean system by following commands:

1. sudo apt-get clean
2. sudo apt-get autoclean
3. sudo apt-get autoremove

then log-off and check to sure if XFCE is un-installed properly & LXDE or anyother DE is installed for account already!.
Then install XFCE again by using:

sudo apt-get install xubuntu-desktop

I hope that may help you somehow!

Source: Experience with LXDE (Lubuntu desktop Issue).

---

### Post by LukasLeon on 2014-05-12
Hey, thank you very much for your answer! I am just a total newbie to desktop enviroments of Linux (i am using Linux itself for a few months now) so i have a few answers, just to make sure i wont screw something up. When i install LXDE, how do i "active" it, so it will be used instead of XFCE? And if i just uninstall XFCE without having any other DE installed, will my computer be able to boot up? Will it boot into command line where i am gonna be able to install the XFCE again? Thanks again.

> **Muhammad_Ahmad_Mujtaba said:**
> i don't know what is the solution to this problem but i recommend 'Synaptics Package Manager' to remove all about XFCE but before doing so install LXDE [Lightweight Environment] and see if such problem is there ? If so? then there's no good in re-installing desktop environment.

To remove Xfce completely without troubles, open Synaptic Package Manager and click Sections > Installed. In search box, type environment name eg 'Xfce' and all Xfce packages would appear. Select all of them > Mark for complete Removal (recommended) or Mark for Removal (which will leave packages .deb on you filesystem somewhere for future which is not good for re-installing as some bad package remain there and again cause problem)
and hit 'Apply'.
Wait for when it's done. . . Now an extra but useful step is to clean system by following commands:

1. sudo apt-get clean
2. sudo apt-get autoclean
3. sudo apt-get autoremove

then log-off and check to sure if XFCE is un-installed properly & LXDE or anyother DE is installed for account already!.
Then install XFCE again by using:

sudo apt-get install xubuntu-desktop

I hope that may help you somehow!

Source: Experience with LXDE (Lubuntu desktop Issue).

---

