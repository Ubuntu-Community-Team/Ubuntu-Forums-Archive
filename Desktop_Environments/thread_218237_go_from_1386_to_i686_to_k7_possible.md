---
title: "go from 1386 to i686 to k7 possible?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by kazuya on 2006-07-18
I have an AMD 64 bit 3800 CPU with i Gig of RAM, but I am only running the Ubuntu LTS 386 version. Can I convert my install from an i386 to an AMD or k6/ k7 or 686 version

I have another PC with AMD 2500, can I change my install type from i386 to 686 or k6? How do I do it and how efficient would things run?

Do I need to reinstall everything already installed so that they can take advantage of my CPU/

I used the PC version for my AMD 64 since I heard multimedia is difficult to have working on the 64bit version of Ubuntu LTS install CD.

---

### Post by reacocard on 2006-07-18
no reinstall nessecary. just search synaptic for linux-image and install the appropriate kernel. i have a pentium m and the 686 is definitely faster than the 386. for an athlon, you want k7 for the best effect.

---

### Post by kazuya on 2006-07-18
how do you install 686 image via synaptic, is there a guide somewhere here on how to do it. I remember following one before. Are there two things only to install, like header, image.. What about nvidia already installed via automatix?
Do I need to run automatix again?

---

### Post by compuguy1088 on 2006-07-18
All you really need to do is to search in Synaptic under linux and scroll down the list until you reach linux-image, there should be the latest k7 and 686 kernel there, for the restricted monduels, you'll have to search for that  separately, all you don't want to do is to delete the kernel your using now, because you can't until you install the 686 or k7 kernel.

---

### Post by asplode on 2006-07-18
```
sudo apt-get install linux-686
```
or
```
sudo apt-get install linux-k7
```
done.

---

### Post by dthiery on 2006-07-18
When I did the default install of 6.06 on my AMD XP1800+ it installed the k7 kernel by default.  You may want to check to see if it did the same for you (uname -a).

Dave

---

### Post by kazuya on 2006-07-25
thanks. I installed linux-686 image and all the 686 restricted modules and newest 686 kernel. I notice somewhat more speed with 686 than k7 on my athlon XP 2200.

I do not understand why? I thought k7 would work best for my AMD machine than 686. Any ideas why 686 appears to run my desktop faster?

Also is there a way to make system response time even faster besides prelinking.? Does having xubuntu, kubuntu, and gnome desktops, and fluxbox make my system slower to do tasks regardless of what desktop I select? Would system be much faster if I had just ubuntu desktop or kubuntu or fluxbox only?

---

