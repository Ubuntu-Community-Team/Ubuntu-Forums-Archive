---
title: "nvidia-glx-new on 8.04 and packages"
date: 2008-12-11
forum: General Help
---

### Post by Sadistic Tribble on 2008-12-11
Just got my new HDD (w00t), and installed my old copy of Ubuntu 8.04. nvidia-glx-new drivers won't enable, and I completely forgot how I got them the last time. I tried getting them in synaptic but it can't install anything- says 
[INDENT]"XXXXX cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type".[/INDENT]
 It says this for every package, actually. I tried sudo apt-get install nvidia-glx-new, but it says
[INDENT]"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate".[/INDENT]

So... can I get the drivers, or do I need to tackle this package installing thingy first? :confused:

---

### Post by nzadLithium on 2008-12-11
what card do you have? and what processor?

---

### Post by Sadistic Tribble on 2008-12-11
GeForce 8600 GT, Intel Core 2 Duo E4500. :popcorn:

---

### Post by nzadLithium on 2008-12-11
I think maybe your downloading from wrong repos? Did you change them recently? :S

---

### Post by SmokinJuan on 2008-12-12
System>Administration>Hardware Drivers

Then tick the box for the nvidia driver and hit apply.

---

### Post by hikaricore on 2008-12-12
The nvidia-glx-new package is not currently used, instead nvidia-glx-177 is.
I personally don't understand this logic, but I'm not the package maintainer.  :p

---

### Post by nzadLithium on 2008-12-12
hikari i thought that 8.04 still uses the old naming system?

---

