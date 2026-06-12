---
title: "Is Ubuntu Gutsy more memory hungry than the previous versions?"
date: 2007-12-19
forum: Desktop Environments
---

### Post by PryGuy on 2007-12-19
Good day everyone! I have a poll here. I have installed Ubuntu Gutsy on my office machine with 256Mb RAM and noticed that it swaps more frequently than Feisty. Am I wrong or Gutsy Gnome 2.20 has bigger appetite for memory?

---

### Post by chewearn on 2007-12-19
Two highest memory consumers in my PC: compiz, deskbar-applet.  Both these were not in default Feisty install.

---

### Post by lswest on 2007-12-19
I haven't noticed much increase in RAM usage...however both my of my computers which run gutsy have 1GB+ of RAM, but (with compiz, awn, etc.) it sometimes goes up to 300MB-400MB with around about 10 applications open... anyways, i don't find it a resource hog, especially after using Vista...

---

### Post by sloggerkhan on 2007-12-19
Not sure if it's using more. I started doing more intensive graphics right about when I switched and all the memory issues I ever have are either related to gimp or to inkscape when I have either large or complex images that I'm working on. (I can easily max out my CPU and my memory in either program.)

If  I don't use those programs, I don't think I'm ever much above 40% of a gb, maybe with a fair amount of the rest used for cache.

---

### Post by chris4585 on 2007-12-19
i cant really say, because last time i had another ubuntu installed was 6.10, and it was on another pc, overall it depends on what you have running

---

### Post by PinkFloyd102489 on 2007-12-19
Here's a tweak you can use to prevent Ubuntu from swapping as much.


Edit /etc/sysctl.conf and add the following to the end of the file:


```

#Swappiness
vm.swappiness=0

```



This will force the system to use as much of the RAM as possible before it starts swapping. It wont use ALL of the RAM, but a good portion.

---

