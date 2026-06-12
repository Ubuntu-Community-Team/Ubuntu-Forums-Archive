---
title: "please help..."
date: 2009-11-12
forum: Desktop Environments
---

### Post by B_smoke on 2009-11-12
hi i'm new to ubuntu and i have to say i like it very much.
but there is something that's bugging me non stop.
i want to change my visual effects on my desktop to extra but when i do that, i get desktop effects could not be enabled .
i know already that this has something to do with my graphic card drivers at least i think so...
so i downloaded the drivers from the nvidia site (i have a nvidia Geforce 8500GT) but i have no idea how to install them.
and i've tried to look in the system-hardware drivers to look for them but there stood nothing except at the top it said "no proprietary drivers are in use on this system".

can someone please help me with this,i'll be very gratefull

p.s: sorry if my english is crap, i'm from belgium ;)

---

### Post by undecim on 2009-11-12
According to [http://packages.ubuntu.com/karmic/nvidia-glx-173](http://packages.ubuntu.com/karmic/nvidia-glx-173), the nvidia-glx-173 package provides support for that card.

Try installing "nvidia-glx-173" from System -> Administration -> Synaptic Package Manager

Or, you can open a terminal and run this command:```
sudo aptitude install nvidia-glx-173
```

---

### Post by B_smoke on 2009-11-12
thank for the tip but i already solved it out myself, it took me a few hours but now i will remember it for the rest of my life :p

---

### Post by ikt on 2009-11-12
> **B_smoke said:**
> thank for the tip but i already solved it out myself, it took me a few hours but now i will remember it for the rest of my life :p

what did you do?

---

