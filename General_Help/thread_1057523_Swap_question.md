---
title: "Swap question"
date: 2009-02-01
forum: General Help
---

### Post by Mr Rough on 2009-02-01
I managed to look over my swap stuff today and I'm wondering what is normal.

I can run a TON of stuff on 2 GB of ram and it nearly all runs in physical memory. I ran all sorts of things includuing two instances of WoW before it just started to use any swap.

```

$ free
             total       used       free     shared    buffers     cached
Mem:       2071712    1983340      88372          0      32144     664304
-/+ buffers/cache:    1286892     784820
Swap:      5735164       2144    5733020


```

Is this fine since physical memory normally performs better than swap or should I consider switching?

This is also the first time I noticed that my swap was so large. I will resize it to probably 1GB vs 5GB. I'm just not used to other Os' having such low usage of swap so I ask.

Any opinions? Thank you for your time.

---

### Post by mgol on 2009-02-01
At mine Ubuntu (Hardy) starts to use swap when the physical memory is used in about 50%.

There's no need to make 5GB swap - it's really huge! Usually, nowadays it is advised to make swap of size about 50%-100% of actual memory. If You want to use hibernation and/or suspend, at least the RAM size is required - in Your case, 2GB.

---

### Post by Yellow Pasque on 2009-02-01
> I'm just not used to other Os' having such low usage of swap so I ask.
When I first switched over from Windows, I was delighted by Linux's efficient use of virtual memory. Windows (at least XP) manages virtual memory like it's allergic to RAM.

> I will resize it to probably 1GB vs 5GB.
Unless you're running short of disk space, I would recommend that you don't resize partitions, especially if you don't have your data backed up. Also, if you start running low on disk space, it would probably be a better idea to add storage if financially feasible.

---

### Post by Mr Rough on 2009-02-01
I'm not sure why it's 5GB to begin with. I used default settings, just seems odd.

I may resize the partition to just give more space to the system, even though it doesn't really need it. My home partition is a separate hard drive.

I still find it odd that under nearly all loads except the unreasonable, the swap is empty. Even under a situation that will probably never happen, it's only using 2 MB.

Is this common?

---

### Post by Yellow Pasque on 2009-02-02
> Is this common?
Yes, Linux maps as much of your virtual memory cache into physical RAM as possible, for the sake of performance. With 2 GB of RAM, the default settings will work best for you and I would recommend not changing anything. 

FYI, you can control the "swapping" to some extent using the swappiness setting. Nerdy kerneltrap.org thread on this: [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by Sorivenul on 2009-02-02
Adjusting swappiness is the way to go here. I'd link to the KernelTrap article, but see it has already been done...

I haven't touched swap on my Ubuntu install in a long time, but I do very few memory intensive operations and use fairly minimal applications as I have a custom install. Most of the intense work is reserved for FreeBSD, which is another story.

---

