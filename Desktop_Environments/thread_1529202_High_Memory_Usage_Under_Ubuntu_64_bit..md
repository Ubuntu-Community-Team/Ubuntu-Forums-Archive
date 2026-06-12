---
title: "High Memory Usage Under Ubuntu 64 bit."
date: 2010-07-11
forum: Desktop Environments
---

### Post by infamous-online on 2010-07-11
Hi all,

My problem seems to be very simple, it's high memory usage. I occasionally will use movie player to watch a few shows and I use firefox as well. My memory usage starts out real small about 500 mb but after using firefox lightly and movie player it jumps to almost 2 gigs and this is after they've been closed what gives? I've attached an image so you can see what I'm talking about.

---

### Post by cj.surrusco on 2010-07-11
It would be more helpful if you showed the "processes" tab from the system monitor, with the processes sorted by highest RAM usage.

---

### Post by infamous-online on 2010-07-11
Ok, I went to do that and now my mem usage is around 900 mb, weird, all I have running is apache & mysql and firefox and move player when I use it. I just wish I knew what causes the high memory spikes!

---

### Post by lovinglinux on 2010-07-12
I don't see anything wrong with your memory usage. I also have Ubuntu 64bit and I'm currently using 740Mb and I have Firefox, Dolphin and Kate opened. Is not uncommon to see my memory usage over 1.4Gb.

Your Firefox memory usage is perfectly normal. A clean profile uses about 40Mb, while a profile like mine, which has over 60 extensions installed uses about 200Mb. So 88Mb for Firefox is absolutely normal. It would be a problem if Firefox was using like 600Mb or more. If that happens, then you could have an extension leaking memory. Additionally some web sites cause high memory usage. For instance, when I'm editing the layout of my blogs in Blogger, it opens new mini windows for each widget and those increase memory usage a lot (probably DHTML). 

You might want to limit Firefox memory usage, by changing the preferences in about[noparse]:[/noparse]config. Type **about[noparse]:[/noparse]config** in the address bar, then type **browser.cache.memory.capacity**, right-click on the result and select the option modify, then change the value to **14336**. That will limit the amount of memory allocated to Firefox caching system according to your memory capacity.

---

### Post by infamous-online on 2010-07-12
It can't be firefox, because I have Ubuntu on a 32 bit sys and it never goes anywhere near 1 gig, let alone 2 so it has to be something else. I even tried a whole day without any browsers and the mem usage will spike up to almost 2 gigs, so it's gotta be movie player, is there some way to tweak it?

---

### Post by lovinglinux on 2010-07-12
> **infamous-online said:**
> It can't be firefox, because I have Ubuntu on a 32 bit sys and it never goes anywhere near 1 gig, let alone 2 so it has to be something else. I even tried a whole day without any browsers and the mem usage will spike up to almost 2 gigs, so it's gotta be movie player, is there some way to tweak it?

64bit uses more memory than 32bit. That's how it works.

Anyway, when you notice the memory is spiking, go to System Monitor to find out which application is using too much RAM. Your screenshot is from a normal situation, so there is no way to tell what is going on.

Anyway, you could try this to clear the memory:

```
sudo echo "ready" && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

---

### Post by Grenage on 2010-07-12
That's about the same as my system, and quite normal for an x64 install.  Remember that the computer will use memory if it's there - that's the whole point of RAM!

I'm currently using 1.5GB RAM (out of 4), but little of that is active.

---

### Post by Bluesan on 2010-07-12
OpenJDK that you get through the Medibuntu repositories, was a runaway train once in a while shortly after booting (it was often enough to be predictable).

My solution was to uninstall it, and then to install Sun Java 6. That seemed to have solved the problem, for me at least, though your mileage may vary.

---

