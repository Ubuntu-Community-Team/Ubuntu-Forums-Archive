---
title: "package dependency problem"
date: 2012-01-19
forum: Desktop Environments
---

### Post by motomixon on 2012-01-19
Hello All,
I'm using 11.10 on a generic PC.

Lately, when I am prompted to update my computer, or when I run Update Manager, I find two recommend updates for which I cannot however tick the checkbox: "architecture independent files for Evolution (installed version 2.32.2-0ubuntu7)" and "standard plugins for Evolution (installed version 2.32.2-0ubuntu7)

I am also having troubles with editing my menu bar (at the top), and in trying to fix that using apt-get got an error message that pointed to the two files mentioned above. Unfortunately, I no longer remember what I did and cannot replicate the error. But it gives me added incentive to fix my first problem.

Also, I tried installing Evolution (no, it is not installed), hoping that by then immediately uninstalling it, I could fix my problem. But I get the error: "Package dependencies cannot be resolved" // details: "evolution: Depends evolution-common(=3.2.1-0ubuntu1) but 3.2.1-0ubuntu1 is to be installed"

Luckily rignt now my system is stable, but even so I'd like to fix this so as to eliminate one possible reason for my menu edit problem. (Probably no connection:confused:  )
TIA

---

### Post by cortman on 2012-01-20
Don't know if it has anything to do with your menu editing problems, but the commands


```
sudo apt-get update
sudo apt-get install -f

```

should fix your dependency problems.

---

### Post by motomixon on 2012-01-21
Thanks for the tip, but that didn't change anything.

I am waiting for SpiderOak to complete all my backups, and then I will try removing Xorg and reinstalling it.

---

