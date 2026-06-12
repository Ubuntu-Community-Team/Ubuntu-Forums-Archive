---
title: "CDemu"
date: 2006-09-24
forum: Desktop Environments
---

### Post by ScarFreewill on 2006-09-24
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/) looks like a realy nice app will someone show me how to compile it. (Makefile:31: *** You'll need sources for your (at least 2.6.16) kernel.  Stop.) This is the problem I have. btw I have got linux-image-i368 installed...

---

### Post by reacocard on 2006-09-24
try
```
sudo apt-get install linux-headers-`uname -r`
```
then compile it again.

---

### Post by towsonu2003 on 2006-09-24
> **ScarFreewill said:**
> [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/) looks like a realy nice app will someone show me how to compile it. (Makefile:31: *** You'll need sources for your (at least 2.6.16) kernel.  Stop.) This is the problem I have. btw I have got linux-image-i368 installed...

I see someone already gave the response :) if it tells you you need other stuff (say xyz), search for its name on synaptic and install xyz**-dev** package.

---

