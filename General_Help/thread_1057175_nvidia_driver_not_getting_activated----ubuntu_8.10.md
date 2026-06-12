---
title: "nvidia driver not getting activated----ubuntu 8.10"
date: 2009-02-01
forum: General Help
---

### Post by shilpiharish on 2009-02-01
Recently i have installed ubuntu 8.10 version.

My problem is, NVIDIA accelerated graphics driver version 177 (recommended) is not getting activated.
I tried to activate the driver by [COLOR="Red"]system > administration > hard drvers > activate,  but many a times the Downlading and Installing window appears but the progress was never crossed 0%. and a error window will get opened after a few seconds.

I tried to get a suitable nvidia driver package from the net, It carries a name like............. NVIDIA-Linux-x86-100.14.19-pkg1.run.........I tried this file to run through the root but it was not installed too.

I request you people to let me know how shall I resolve the above mentioned problem.


Details of PC:

system: hp pavilion
model: dv 6000
1 GB RAM
processor: AMD TURION(64X2)
compatible driver:NVIDIA Corporation GeForce 7150M(rev 2) 


regards 
harish

---

### Post by taurus on 2009-02-01
> and a error window will get opened after a few seconds.
What is the error message?

---

### Post by shilpiharish on 2009-02-01
It is just a window with a red bubble.

I mean the downloading and installation of the driver get stopped.

---

### Post by photon_man62 on 2009-02-01
Close every other window (especially package managers) and THEN try activating it.

I had that problem once.

---

### Post by shilpiharish on 2009-02-01
@photon_man
thanks for our reply.

I tried the same thing what you suggested. I closed all the windows but still the driver is not activated.

---

### Post by photon_man62 on 2009-02-01
Then I have no idea what the problem may be.

Maybe you are NOT the root user?

---

### Post by fragos on 2009-02-01
Open a terminal window and run:

sudo apt-get install nvidia-glx-177

This will give you details about any download problems. You'll still need to use preferences as above to select the driver for use.

---

### Post by taurus on 2009-02-01
Make sure the update manager is not running in the background, updating your machine.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by shilpiharish on 2009-02-01
@fragos

than-Q very much. The problem was completely resolved after running it in terminal window.

---

