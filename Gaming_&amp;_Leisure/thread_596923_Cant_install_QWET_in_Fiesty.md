---
title: "Cant install QWET in Fiesty"
date: 2007-10-30
forum: Gaming &amp; Leisure
---

### Post by The Populist on 2007-10-30
I just downloaded the Quake wars demo. When I try to install it, I get this message:

"Cannot open /home/*********/Desktop/ET...mo-client-1.1-full.r5.x86.run: No application suitable for automatic installation is available for handling this kind of file."

Can someone provide a terminal command or something so I can install this?

...

---

### Post by Persian_Sniper2000 on 2007-10-30
i have orginal DVD , but when i want install it , says : it's not runing on win95/98/nt/2000 ... i using 7.10 and Wine 0.9.47 
thats not cool :( :mad:

---

### Post by Dapilot1 on 2007-11-01
To install the full game from a windows dvd, follow the guide here.

HowTo: Install ETQW Full on Gutsy
[http://ubuntuforums.org/showthread.php?t=583762&highlight=quake+wars](http://ubuntuforums.org/showthread.php?t=583762&highlight=quake+wars)

The easiest way to install from a .run is to copy and paste this code into the terminal.
```
sudo sh 
```
Then hit space and drag and drop the .run from where ever you have it into the terminal.

---

### Post by Crafty Kisses on 2007-11-01
> **Dapilot1 said:**
> To install the full game from a windows dvd, follow the guide here.

HowTo: Install ETQW Full on Gutsy
[http://ubuntuforums.org/showthread.php?t=583762&highlight=quake+wars](http://ubuntuforums.org/showthread.php?t=583762&highlight=quake+wars)

The easiest way to install from a .run is to copy and paste this code into the terminal.
```
sudo sh 
```
Then hit space and drag and drop the .run from where ever you have it into the terminal.

That should do it, please post back. :KS

---

### Post by SM0k3 on 2007-11-02
I was trying to install this also, the method posted above worked for me but at first I was getting a "Permission Denied" error which I fixed by just going into "ETQW-demo-client-1.1-full.r5.x86.run" properties and checking "allow executing file as program".

Thanks

---

### Post by omega_user on 2007-12-13
I was wondering if the full DVD version would work in 7.06.  I have the demo and it's fully functional but I'd like to get the full quality game.  Would the Gutsy instructions work just like the Fiesty ones? or should I upgrade to Gutsy (I only haven't because I'm worried my newer graphics card won't be supported

---

### Post by Beren Camlost on 2007-12-13
> **omega_user said:**
> I was wondering if the full DVD version would work in 7.06.  I have the demo and it's fully functional but I'd like to get the full quality game.  Would the Gutsy instructions work just like the Fiesty ones? or should I upgrade to Gutsy (I only haven't because I'm worried my newer graphics card won't be supported


The procedure should be exactly the same for Feisty and Gutsy :KS

---

### Post by DarwinsTheory on 2007-12-14
I got both the demo and full game working fine in Fiesty...

Followed the howto in the forum and bang it came up no worries...

Only hassel I had was it wouldn't use 5.1 sound.. kept wanting to go stereo.

Changed my launcher to this
/home/matthew/Games/ETQW/etqw +set s_driver alsa

Problem resolved.

Matt

---

