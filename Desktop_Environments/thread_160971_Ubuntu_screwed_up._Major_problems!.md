---
title: "Ubuntu screwed up. Major problems!"
date: 2006-04-16
forum: Desktop Environments
---

### Post by Mr Egg on 2006-04-16
Hey, I installed Ubuntu and today while editing xorg.conf Ubuntu wouldnt boot. So I deleted the partition and inserted the microsoft disc and fixmbr'ed. Now, when I try to install Ubuntu the installation goes really REALLY slow, and when I get to the "Setting up the partitioner" section, it freezes. How can I fix this?

P.S. I tried it with 2 different discs. Same result.

---

### Post by bikeboy on 2006-04-16
Did you only have 1 Ubuntu partition or do your have separate / and /home partitions? If the latter, there may be info in /home that is causing the problem perhaps.

Could you show us a full list of all your current partitions?

---

### Post by Mr Egg on 2006-04-16
Well, from what I can tell. I had a 80GB Partition (My Windows) and a 20GB partition (Ubuntu) and a 1GB Partition (swap). I deleted the Ubuntu and swap partition but problems still persist. Could it be GRUB still installed? Please help, I really like Ubuntu and I wan't to get it back up and running. I was working on developing a program and now I've lost all my hard work :-|

Oh, I must point out something, it may be important. Before I deleted the Ubuntu partitions, when I tried to boot into Ubuntu it got stuck at the "Loading modules" or "Initializing modules" I can't remember which one.

---

### Post by bikeboy on 2006-04-16
[QUOTE=Mr Egg] Could it be GRUB still installed?[/QUOTE]

Seems unlikely as you fixed the mbr. But maybe, what method did you use for the fix. I think you can do it from the Windows cd or from safe mode. I haven't done it before though so that's as far as my knowledge goes. Some other threads about grub problems might shed some more light on it.

---

### Post by Mr Egg on 2006-04-16
Don't worry, I fixed it now. I had to pull out some unneccesary peripherals.

---

### Post by bikeboy on 2006-04-16
Haha, it always ends up being something silly and simple. Glad you got it sorted.

Bikeboy

---

