---
title: "CPU Useage"
date: 2009-02-09
forum: General Help
---

### Post by Funky91 on 2009-02-09
Hi, I installed Ubuntu 8.04 on my PC the other day and today I noticed that the CPU useage hardly ever goes below 30% on both cores.

I did a bit of googling and found that this can be to do with the update notifier so I ended that process and it stayed about the same, I then disabled compiz and turned off the dock (cairo-dock) with no luck.

Im running the latest drivers for my graphics card (nVidia Version 177).

The only performance issue I have noticed is that when playing mp3s on Totem it seems to occasionally skip.

Im conscious that this can't be good for the life of my processor. What could be causing this?

---

### Post by cb951303 on 2009-02-09
my cpu comes and goes between 15-40% (both cores). I don't think there is something wrong. This is probably how its supposed to be.

---

### Post by konny77 on 2009-02-09
Um why dont you check which process is actually causing the load? Type
```
top
```
into a terminal.

---

### Post by cb951303 on 2009-02-09
> **konny77 said:**
> Um why dont you check which process is actually causing the load? Type
```
top
```
into a terminal.

Or "System Monitor" > "Processes"

EDIT: Lol system monitor uses 15-20%. That might be the problem

---

### Post by Funky91 on 2009-02-09
> **cb951303 said:**
> Or "System Monitor" > "Processes"

EDIT: Lol system monitor uses 15-20%. That might be the problem

Ah, you may be right about that one! Silly me. Besids that xorg seems to be the main offender but I doubt theres much we can do 'bout X.

Thanks

---

