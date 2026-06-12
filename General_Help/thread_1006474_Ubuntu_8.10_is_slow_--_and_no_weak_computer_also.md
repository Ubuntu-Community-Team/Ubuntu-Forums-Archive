---
title: "Ubuntu 8.10 is slow -- and no weak computer also"
date: 2008-12-09
forum: General Help
---

### Post by Arnitak on 2008-12-09
I have a Quad Core, Q6600 with 4 Gigs of RAM which I use as a dev platform. Why is rails so slow? As soon as I got two remote ssh sessions open, switching between tasks and the like, takes one second or so. Windows Vista x64 is more rapid than Ubuntu. My take is that Ubuntu is to bloated, any ideas?

---

### Post by cmnorton on 2008-12-09
You'll need to see what's running. Either look at the output of top or ps -ef.

Is everything slow or just rails?

---

### Post by Arnitak on 2008-12-09
> **cmnorton said:**
> You'll need to see what's running. Either look at the output of top or ps -ef.

Is everything slow or just rails?

How'd you know I play with rails? :D

No, I dont use this machine for rails.

Only one CPU is at 95% all the time, the rest are free.

---

### Post by linuxvacuum on 2008-12-09
I always blame GNOME :tongue:. Try a fast window manager such as the wonderful fvwm-crystal and see if the speed is improved. If not, then it's probably the powernowd daemon. 

Actually, try this first before changing your window manager:
```
sudo /etc/init.d/powernowd stop
```

---

### Post by Arnitak on 2008-12-09
How would I switch a window manager to fwm-crystal?

---

### Post by Arup on 2008-12-09
Do you have compiz turned on? Go to system>appearance and select effects to none and then turn on gnome metacity. Not only will Ubuntu be snappy, the dreaded screen going blank after logging in would be gone as well.

---

### Post by Arnitak on 2008-12-09
> **Arup said:**
> Do you have compiz turned on? Go to system>appearance and select effects to none and then turn on gnome metacity. Not only will Ubuntu be snappy, the dreaded screen going blank after logging in would be gone as well.

I've got no dreaded screen that goes blank.
Why would I turn off the effects? After all, I have 4 processors ...
I see using top that X uses 60% of the cpu's which is strange. And firefox handles the rest 39% ... strange.

---

