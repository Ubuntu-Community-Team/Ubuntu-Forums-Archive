---
title: "RAM troubles"
date: 2005-02-05
forum: Desktop Environments
---

### Post by totalshredder on 2005-02-05
Hey Everybody,

   I just installed Ubuntu, and I love it, by far my favorite out of the box distro.

   Anyways, I'm having some problems with my RAM, I am using 100% of my RAM(with firefox open) but I have 230 MB of RAM(I only have firefox running!!). Is there anything I can do to shrink the amount of RAM I am using? I have tried going into System Monitor and closing down some un-needed aps, but to no avail. It says that 45% of the memory I am using is cache, is there any way I could bring my cache down? Or make it so it uses the swap more? I also am unable to use any OpenOffice programs. 

Thanks, for *any* help you can give me!!

God Bless,
Luke Demi

---

### Post by az on 2005-02-05
How much ram is used just after you boot?

Are you swapping out a lot, or has this just been a problem since you looked at how much ram you are using?

I do not think that this is alarming, if there is no reason for it to clear out the cache, why should it?  It does not mean that you are going to start swapping.

---

### Post by AndersAA on 2005-02-05
how are you checking how much ram you are using?  Linux should always use all your ram, it caches aggressivly.  Free -m is also not accurate, aslong as it doesn't swap, you're doing fine :)

---

### Post by valadil on 2005-02-05
gnome-system-monitor is not an accurate way of seeing how much ram is being used up.  This isn't the best explanation, but think of it as the ram thats reported by gnome-system-monitor is what programs have claimed for themselves, though they won't actually use it.  They ask for more ram than they actually need and give some back if the system needs more for other things.  

My system for instance, is claiming to be using about 985mb of ram because I've got a gig.  If I take out one of the 512s it goes down to using 490ish mb at any given time and doesn't run any differently.

---

### Post by az on 2005-02-05
cat /proc/meminfo.

---

### Post by rwabel on 2005-03-02
Well my system runs quit slow. Even having 1GB of RAM and Athlon XP 2200.
I dont' know if it's a problem having mounted several fat32 parititions on my system.
CPU Usage is normal and low but my memory usage is high.
I tried to find out with cat /proc/meminfo, but I don't know if that's now good or bad or normal. I've made also a swap partition, but I don't know if the swap partition is ever been used.

rwabel@RALPH:~/compiling/ $ cat /proc/meminfo
MemTotal:      1036484 kB
MemFree:         10376 kB
Buffers:         16132 kB
Cached:         154344 kB
SwapCached:          0 kB
Active:         890956 kB
Inactive:        90152 kB
HighTotal:      131008 kB
HighFree:          336 kB
LowTotal:       905476 kB
LowFree:         10040 kB
SwapTotal:           0 kB
SwapFree:            0 kB
Dirty:              20 kB
Writeback:           0 kB
Mapped:         868316 kB
Slab:            25924 kB
CommitLimit:    518240 kB
Committed_AS:  1604688 kB
PageTables:       5636 kB
VmallocTotal:   114680 kB
VmallocUsed:      8256 kB
VmallocChunk:   105236 kB

[QUOTE=azz]cat /proc/meminfo.[/QUOTE]

---

### Post by totalshredder on 2005-03-04
Hey Everyone,

   OpenOffice ended up working well for me, and my misconceptions became fixed (thanks!)

 BUT, I reinstalled ubuntu (damn horay bugs) and now I cannot open OpenOffice... it flickers a little (It kind of half looks like it's opening...) but it doesn't actually start up. I'm thinking of doing an apt-get and completely re-installing it, but I'm wondering if there's an easy fix. Thanks a lot!

Luke Demi

---

