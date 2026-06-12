---
title: "help me please ati compiz"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by mrmarks on 2008-03-03
[B]help me please i am pretty new to linux but not to basic programing 
ive been searching on this subject for a while 
i have a connect3d radeon 9550
 1 gig of ram
 i am running gutsy on a dual boot with xp sp2
i cannot get compiz-fusion to run 
can someone please help me 
let me know if you need to know anymore info 
can i please have a simple step by step guide 
thank you so much in advance for any info provided
:-)[/B]

---

### Post by Afkpuz on 2008-03-09
1.) Install Video drivers

Goto System=>Administration=>Restricted Drivers Manager

Check the box next to your video card to install drivers.  Don't reboot yet.


2.) Install xserver-xgl and compiz settings manager

Goto a terminal
Application=>Accessories=>Terminal

Paste this into terminal (the command for pasting into terminal is ctrl+Shift+v)
```
sudo apt-get install xserver-xgl compizconfig-settings-manager
```

Reboot, then try enabling desktop effects

---

