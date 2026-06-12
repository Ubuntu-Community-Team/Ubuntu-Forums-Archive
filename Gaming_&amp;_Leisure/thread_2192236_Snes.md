---
title: "Snes"
date: 2013-12-06
forum: Gaming &amp; Leisure
---

### Post by steve8 on 2013-12-06
Hello everyone, I was wondering if anyone has found a fix for the zsnes emulator.....really getting on my nerves how it freezes everytime I use it. I tried downloading higan
the updated bsnes emulator and it works okay but i been wanting to play final fantasy 5 again. With that game i like to have a turbo key to speed up the battles when leveling 
up but, unfortunately the turbo function doesn't actually work. I also noticed software center doesn't have snes 9x which is the one I used to use and probably the best. Anyone
got any ideas?

---

### Post by LillyDragon on 2013-12-06
What package of ZSNES are you using? There isn't one for 12.04 in the Software Center and beyond as far as I know. I had to go to Synaptic Package Manager and use the 32-bit version available there; it's pretty stable on my machine.

I can't speak for SNES9X, since I never got it to work on my installations, but BSNES is pretty solid if you can configure it properly. You could probably tweak the settings to make the game play much faster for certain segments, but it's not as easy as toggling it with a button.

---

### Post by steve8 on 2013-12-06
ye i downloaded it through synaptic package manager too
i386 version 1.510+bz2-5ubuntu

i can play it for about half an hour then it just freezes i cant even kill it through task manager i have to hold down the power button to restart i notice it also does it if i hit escape to bring up the emulator menu and leave for a few minutes.

---

### Post by neural_adapter on 2013-12-11
Bsnes has a turbo function. It is mapped to the tilde key per default. In my experience Bsnes is the superior emulator.

---

### Post by aisyk-neuf on 2013-12-23
Hi, there is a ppa for snes9x-gtk.
[https://launchpad.net/~bearoso/+archive/ppa](https://launchpad.net/~bearoso/+archive/ppa)

You have two choices :
Download directly the file .deb and install it
Add PPA source to your Software Center (for automatics updates)
(in a terminal you can write theses commands : "**sudo add-apt-repository [B]ppa:bearoso/ppa**[/B]" and "**sudo apt-get update && sudo apt-get install snes9x-gtk**")

---

