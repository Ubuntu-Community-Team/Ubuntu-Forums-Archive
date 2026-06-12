---
title: "Problems with Nvidia GeForce 6600 in 9.04"
date: 2009-05-04
forum: General Help
---

### Post by Crimson Kaze on 2009-05-04
When i start up Ubuntu, it usually displays errors and tells me to go into low graphic mode. then after that i end up at a blue screen telling me that there "appears to be an xserver running on display :O" and gives me a yes or no option. no takes me back to that same blue screen whil yes brings me to a black screen with the mouse cursor. Does anyone know how to fix this problem?

Xorg.0.log
[http://pastebin.com/m3647c1ae](http://pastebin.com/m3647c1ae)

Xorg.conf
[http://pastebin.com/m6b83b048](http://pastebin.com/m6b83b048)

---

### Post by brettg on 2009-05-04
I've had some nvidia problems with the jaunty upgrade.

My solution is to remove the nvidia drivers

sudo apt-get remove nvidia-glx

Reboot your system

Then make sure the dist-upgrade has completed;

sudo apt-get dist-upgrade

Maybe do another reboot

You should have an error free gui based on the open source drivers at this point.

re-install the nvidia drivers

sudo apt-get install nvidia-glx

Reboot again!

Good luck!

---

