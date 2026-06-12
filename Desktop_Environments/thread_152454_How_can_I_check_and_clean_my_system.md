---
title: "How can I check and clean my system?"
date: 2006-03-29
forum: Desktop Environments
---

### Post by bpont on 2006-03-29
I've been using Ubuntu for a while, but only recently acquired internet connectivity.  Therefore, some of the packages I've installed weren't corrected set up since apt-get couldn't fetch missing packages from Ubuntu servers to satisfy dependencies, etc.

I want to avoid reinstalling my system.  I simply want to learn how to run some commands that will check the general state of my system, seek out broken or incomplete package installs and correct them, etc.  I would like a healthy and optimized system, but since I only have a 450mhz Pentium III w/ 256mb RAM, I don't think I should do a dist-upgrade, but simply optimize what I already have. 

Any advice is greatly appreciated!

---

### Post by evilgold on 2006-03-29
I think "apt-get -f install" fixes broken packages.

---

### Post by rfruth on 2006-03-29
Reboot and run cron ...

---

### Post by bpont on 2006-03-30
[QUOTE=rfruth]Reboot and run cron ...[/QUOTE]

could you be a bit more specific?  run cron and....?

---

### Post by bpont on 2006-03-30
[QUOTE=evilgold]I think "apt-get -f install" fixes broken packages.[/QUOTE]

This was good...thx

---

