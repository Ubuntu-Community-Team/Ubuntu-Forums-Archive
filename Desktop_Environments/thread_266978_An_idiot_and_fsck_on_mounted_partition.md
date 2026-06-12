---
title: "An idiot and fsck on mounted partition"
date: 2006-09-28
forum: Desktop Environments
---

### Post by kakulacis on 2006-09-28
Hello!

Preamble:
Yesterdey late at night or rather early in the morning i decided to set up NVIDIA beta drivers 1.0-9625. Well,i shouldn't. Somethink went wrong, probably because i'v tried to install drivers from repos, but at that moment i'v had binary driver installed from script (actually i uninstalled it before, but something caused a problem later). Well after install, xorg complained about unknown nodule type and did not load nvidia module at all. Then i noticed, that some libGL modules have symlinks to older driver modules, so i removed them but after restart - system hanged on.

And now idiot on action:
Have performed fsck operations before, but now I RUN FSCK ON MOUNTED FS (loaded into system in recovery mode). Don't know how, don't know why, probably that's because of sleepiness, but that's a fact. And now all i have left is kernel images :mrgreen: 
But sad par t is - i had important files for me there.

Can You recommend some recovery tool or some feasible actions, that could recover my data? ](*,)

---

### Post by hikaricore on 2006-10-17
Assuming you havn't overwritten all or most of that drive by now, i would suggest if you can boot from a windows partition, try: [Stellar Phoenix : Linux]("http://www.stellarinfo.com/linux-data-recovery.htm")

It's not free but there is a demo *cough* and crack *cough*.  Assuming you havn't destroyed what was left of your files already and that there is actually still something there, this is probably a pretty good shot to getting some of your stuff back.  I borrowed it from a friend of mine ;) when I accidently did "sudo rm -fR *" in my home directory...  *slaps forehead*  and that my friends is why humans need sleep.

---

