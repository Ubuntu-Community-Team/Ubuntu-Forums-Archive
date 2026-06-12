---
title: "Random Black Screen in Ubuntu 13.04 Gnome 3.8"
date: 2013-10-15
forum: Desktop Environments
---

### Post by Psyrus on 2013-10-15
Apologies if this has been answered before (I didn't find any exact matches).

I am running Ubuntu 13.04 64-bit on a Dell Latitude E6530. It appears my issue lies with Gnome 3.8.3. I don't have the same issue with Unity. 

Essentially, the black screen (screen saver) activates randomly, and requires a number of key presses/mouse clicks to disengage. By random I mean not only when I'm away from my desk, but also while I'm working. Usually also at boot - I usually don't even see the login screen at boot. I am the only user so I can just enter my password and am able to login (the Desktop then appears as per normal)

I suspect it may possibly lie with the Nvidia card (system has a dual Intel & Nvidia setup) 

I would appreciate any advice and assistance here. I apologise for the lack of information, but I honestly don't even know where to begin looking.

---

### Post by Frogs Hair on 2013-10-16
Check Power and Brightness & Lock settings , the time can be changed as to when the screen/monitor turns off .

---

### Post by Psyrus on 2013-10-17
> **Frogs Hair said:**
> Check Power and Brightness & Lock settings , the time can be changed as to when the screen/monitor turns off .

Thanks for the reply. Those were the first settings I changed. At the moment dimming is not active, screen is never turned off when inactive, system only suspends when running off battery(hardly ever), and is set to lock after 1 hour of inactivity.

The issue, however, crops up even when I'm actively using the system.

---

### Post by Psyrus on 2013-10-17
I have been running on Unity since yesterday morning and haven't had any issues yet, so it appears to be Gnome related.

---

### Post by erasmusp on 2013-10-17
This does sound like a driver issue to me. What drivers did you load for your Nvidia card? The ones that came with Ubuntu or the propriety drivers?

---

### Post by Psyrus on 2013-10-17
My memory is a little fuzzy, but I think I did install some propriety drivers (due to Nvidia Optimus). Where would I check this?

---

### Post by erasmusp on 2013-10-17
I've just read another thread on this forum that seems to have the same symptoms as your PC on Nvidia. Could someone who is more familiar with this driver problem jump in here and give suggestion to Psyrus of how to overcome his predicament?

---

### Post by Frogs Hair on 2013-10-17
I'm not running an Optimus driver and if you are running Gnome 3.8 on 13.04 you also have ppa installed which may change how you resolve the problem. 13.10 comes with 3.8 by default.

---

### Post by Psyrus on 2013-10-18
Hmmm...may be a good idea to upgrade to 13.10 then. It seems 3.8 brought with it some instability. I'm experiencing the same issue, albeit less often, with Unity now too. :(

---

### Post by Frogs Hair on 2013-10-18
There is a Optimus/ Bumblebee package in the 13.10 repositories. Description from synaptic:
  
Bumblebee is an effort to make NVIDIA Optimus enabled laptops work inGNU/Linux systems. These laptops are built in such a way that the NVIDIA
graphics card can be used on demand so that battery life is improved and
temperature is kept low.


It disables the discrete graphics card if no client is detected, and start
an X server making use of NVIDIA card if requested then let software GL
implementations (such as VirtualGL) copy frames to the visible display that
runs on the intergrated graphics. The ability to use discrete graphics
depends on the driver: open source nouveau and proprietary nvidia.

---

