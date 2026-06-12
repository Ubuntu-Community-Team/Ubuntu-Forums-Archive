---
title: "Cpu usage."
date: 2011-02-13
forum: Desktop Environments
---

### Post by bloodshot13 on 2011-02-13
What should cpu usage be while surfing,moving windows,moving mouse. Just trying to get an idea if this would be normal for MY pc. I know it's different for every pc, because of specs. When I go to system monitor I notice when I move the "system monitor"window the cpu usage goes to 90-98%. When I just move the mouse it goes to around 40%. Is this my computer or is it ubuntu.

---

### Post by dondiego2 on 2011-02-13
Good question. Every once in a while my computer slows down and I notice that the cpu is maxed out at 100%. This happened Friday when I was installing a bin file for the latest Adobe through the package manager. I let it run and it took forever. I couldn't find any resource hogs so I don't know what was going on. Usually I will reboot and it comes back up fine but I didn't want to kill it in the middle of an installation.

---

### Post by grahammechanical on 2011-02-13
How much memory do you have in your graphic card? How much RAM memory do you have? How big is your swap partition?

Regards.

---

### Post by bloodshot13 on 2011-02-13
Is this it? 3.1gigs swap partition.

---

### Post by bloodshot13 on 2011-02-13
Streaming video(newest snl) cpu runs about 80-85%. running nothing but songs in rhythmbox around 20-25%.

---

### Post by cjhabs on 2011-02-13
Running "top" should show the resource hog.

---

### Post by infamous-online on 2011-02-13
> **bloodshot13 said:**
> Streaming video(newest snl) cpu runs about 80-85%. running nothing but songs in rhythmbox around 20-25%.

I asked this question several months agom but are you running a 64 bit or 32 bit system? A 64 bit system uses more memory than a 32 bit does.

---

### Post by cascade9 on 2011-02-14
@infamous-online- tried reading the sig? "32bit lucid lynx 10.04". 

> **cjhabs said:**
> Running "top" should show the resource hog.

+1. System monitor is also a resources hog, it will be adding quite a bit to the CPU usage. 

I would guess that at least part of the problem could be desktop effects.

---

### Post by bloodshot13 on 2011-02-15
I'm not using any desktop "effects". No compiz type program. Just basic desktop. @cjhabs I'm not sure what "top" is but I've looked in the software center and find htop. Is that it? I've also looked in synaptic and don't see it.

---

### Post by bloodshot13 on 2011-03-03
Well, it was definitely the computer. I have a newly built computer and the system monitor is much,much better. I'm not overclocking or anything(stock everything) and it handles,system monitor and watching hd video on you tube pretty well. Have compiz installed,watching hd video while moving the system monitor window, the cpu usage shows 4(cpu's) that never get above 55%. No skips,lags, or anything. Very nice. Technology amazes me.

---

### Post by Frogs Hair on 2011-03-03
> **bloodshot13 said:**
> I'm not using any desktop "effects". No compiz type program. Just basic desktop. @cjhabs I'm not sure what "top" is but I've looked in the software center and find htop. Is that it? I've also looked in synaptic and don't see it.

Htop appears in the in the 10.10 software center .```
sudo apt-get install htop
```
The program runs from the terminal or from the system tools icon.

---

### Post by bloodshot13 on 2011-03-03
> **Frogs Hair said:**
> Htop appears in the in the 10.10 software center .```
sudo apt-get install htop
```The program runs from the terminal or from the system tools icon.
Thanks!

---

