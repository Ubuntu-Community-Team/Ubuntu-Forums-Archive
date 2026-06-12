---
title: "Kubuntu uses 300+MB ram on fresh install?"
date: 2007-07-03
forum: Desktop Environments
---

### Post by timzak on 2007-07-03
I briefly experimented with Kubuntu on an old Dell laptop and noticed after a fresh install that well over 300MB of ram was in use with no apps running.  Is this pretty much the norm for Kubuntu?  Xubuntu uses about 85MB and Ubuntu around 120MB in the same situations, at least in my experience.

I quickly replaced Kubuntu with Xubuntu on that laptop because it only has 384MB ram.  So I can't go back and experiment with it.

Just wondering if that's the norm for Kubuntu, or maybe I did something wrong?  I'd like to try Kubuntu again, but on a system with more ram.  I have very little experience with a KDE-based distro.

---

### Post by GeneralZod on 2007-07-03
This is a common mistake, due to the way ksysguard reports memory usage.

See e.g. 

[http://ubuntuforums.org/showthread.php?p=2015680#post2015680](http://ubuntuforums.org/showthread.php?p=2015680#post2015680)

For the record, I once accidentally forgot to add a swap partition to a fresh install on my 256MB laptop, and it took quite a long time to run into trouble (I finally had to open up the behemoth that is Eclipse in order to bring it to its knees), so 384MB of RAM is more than sufficient for most tasks.

---

### Post by regomodo on 2007-07-03
try and install htop. 

it's a much better tool of monitoring your memory usage

---

### Post by timzak on 2007-07-03
Thanks,  I'll have to reinstall Kubuntu when I get another chance.  I wonder how they would let a bug like this continue?  It puts Kubuntu in a bad light when someone runs the built-in system monitor and sees over 300 MB in use with no programs running.

---

### Post by GeneralZod on 2007-07-04
> **timzak said:**
> Thanks,  I'll have to reinstall Kubuntu when I get another chance.  I wonder how they would let a bug like this continue?  It puts Kubuntu in a bad light when someone runs the built-in system monitor and sees over 300 MB in use with no programs running.

It's not so much a "bug" as a rather silly design choice; the returned value is a perfectly "accurate" measure of the amount of RAM used, but one that does not really matter to most users: the amount of file cache used is a pretty uninteresting statistic :)

The situation in KDE4 is improved, IIRC: the total RAM used no longer includes cache.  The per-app memory usage is also made more accurate by considering the RES, SHR and X-server memory consumed by the app; I'm not sure if this will over-or-under-report the actual usage compared to GNOME, but it is at least a more meaninful metric.

---

### Post by Happy_Man on 2007-07-04
I have found that when all is said and done, KDE uses about maybe 150 megs of RAM. Perfectly serviceable even on my really really old 256 MB behemoth of a computer.

---

### Post by egonkasper on 2007-07-04
The reason it says it is using so much is because ksysguard as well as the gnome system monitor both include cached data in the memory usage.  If you want to know how much is actually being used subtract the cached amount from the "total" memory usage.  So it is actually a good thing for the memory usage to be high as this means that your programs are cached in memory so they will load fast the next time you use them!  And of course when you need more memory for programs the amount of cached data will decrease to give you more space for running programs.

---

### Post by timzak on 2007-07-05
> **egonkasper said:**
> The reason it says it is using so much is because ksysguard as well as the gnome system monitor both include cached data in the memory usage.  If you want to know how much is actually being used subtract the cached amount from the "total" memory usage.  So it is actually a good thing for the memory usage to be high as this means that your programs are cached in memory so they will load fast the next time you use them!  And of course when you need more memory for programs the amount of cached data will decrease to give you more space for running programs.

I just checked Gnome system monitor and it matches conky's memory usage.  In both cases, I'm using 165MB of ram with Firefox open...nowhere near the 300+MB that ksysguard was showing on a clean install with no programs open.  I guess I need to reinstall Kubuntu so I can try and replicate this and study it more.  At the time, I was looking for an OS for my old laptop and wanted to try Kubuntu since I was already using Ubuntu on my main rig and Xubuntu on my garage media player computer.  I didn't have Kubuntu on my laptop for more than a couple of hours.  It felt sluggish and once I saw that 300+MB usage, I just figured it was meant for higher memory systems, so I ended up putting Xubuntu on the laptop.

For the record, my Ubuntu install uses about 120 MB after a fresh boot and no apps open, and Xubuntu uses about 85 MB in the same situation.

---

