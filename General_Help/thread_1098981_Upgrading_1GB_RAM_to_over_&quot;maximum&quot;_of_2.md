---
title: "Upgrading 1GB RAM to over &quot;maximum&quot; of 2GB?"
date: 2009-03-17
forum: General Help
---

### Post by Greg Xix on 2009-03-17
Love Ubuntu. But both it and Winblows(still use Vista about 10% of the time) run at B-/C+ grade quality but my desktop does lag on occasion on both OS's. I want to Upgrade (namely Memory)because when Jaunty gets released I plan on going from a 32-bit intstall to 64-bit and I'd like to keep up with hardware overall.

I have a 2.8Ghz Dual-Core, 64-bit CPU/Motherboard. But the issue is I have only 1GB of RAM and their specs say can only go 2gb Maximum in my only 2 slots(currently 2 x 512). I would love to go 4GB. Could I in a sense "overclock" and install '2 x 2GB' Ram  in there? And get my beloved 4GB of RAM to work? The warranty is long since over, the computer is about 2 years old but still a good piece of equipment. Would this work? or do I just settle and get the 2GB max(2 x 1GB)?

Here is my computer's official site:

[http://support.gateway.com/s/PC/R/1009407/1009407sp2.shtml](http://support.gateway.com/s/PC/R/1009407/1009407sp2.shtml)


Thanks.

---

### Post by hikaricore on 2009-03-17
If your hardware spec says you can only use 2Gb of ram then you can likely only use 2Gb of ram.
Overclocking (which means changing the clockspeed of the ram/cpu/gpu) would have no effect on the amount of ram you could use.

If you absolutely must have 4Gb of ram I suggest buying a nice midrange motherboard for 75-100$ being sure it fits your case.

---

### Post by mb_webguy on 2009-03-17
A 32-bit architecture can use up to 4GB of memory, and a 64-bit architecture can use up to... well, much more than you can currently cram into your computer.  If you have a 64-bit CPU and a 64-bit motherboard, I can't think of any reason you should be limited to 2GB.

As hikaricore said, overclocking has nothing to do with memory.  Overclocking is increasing the clock speed of your CPU, therefore artificially increasing the CPU speed at the cost of increased heat and risk of failure.

---

### Post by bodhi.zazen on 2009-03-17
> **mb_webguy said:**
> A 32-bit architecture can use up to 4GB of memory

Not true.

32 bit arch can use up to 64 Gb RAM, has been the case for almost a decade.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by jwbrase on 2009-03-17
> **mb_webguy said:**
> A 32-bit architecture can use up to 4GB of memory, and a 64-bit architecture can use up to... well, much more than you can currently cram into your computer.  If you have a 64-bit CPU and a 64-bit motherboard, I can't think of any reason you should be limited to 2GB.

You get into hardware issues. Sure, a 32 bit architecture can address 4 gigs, or 64 if it uses address extension and the OS supports it, but the motherboard may not be built to feed all of that to the CPU. For example, our older machine has only two memory slots, and each of those slots can only accommodate a 128 meg module. So we're limited to 256 megs even though the architecture can address more.

---

### Post by mb_webguy on 2009-03-17
> **bodhi.zazen said:**
> Not true.

32 bit arch can use up to 64 Gb RAM, has been the case for almost a decade.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
Bodhi is right, as usual.  But so am I.  ;)

A 32-bit processor uses 32 bits to refer to the location of each byte of memory. 2^32 = 4.2 billion, so a 32 bit memory address can only refer to 4.2 billion unique locations.  That means a 32-bit processor can only directly access 4GB of byte-addressable memory.

Physical Address Extension (PAE), however, allows a compatible OS to map the normal 4GB of memory addresses onto a maximum of 64GB of physical memory.  The Linux kernel has supported PAE since 2.6.  I may be wrong, but I don't think the kernel used by 32-bit Ubuntu has this enabled by default, meaning it supports a maximum of 4GB of physical memory.

---

### Post by bodhi.zazen on 2009-03-17
No, but PAE is enabled on the server kernel (or one can recompile).

---

### Post by alex2399 on 2009-03-17
First check if you still have warranty, and if you still have it you are allowed to open the case and install new memory without losing it. If no more warranty, go ahead

Next, look up if you really need it by using the system monitor and doing your everyday tasks, check it when it lags and see if the memory is full.

Only then decide if you spend your money on memory hardware. Also going from 32-bit to 64-bit is not really needed, and will give you some software compatability problems, but those can be solved more or less.

Above is what I would do first for your own conscience, but from looking at your system, yes it looks like 2GB would be nice, especially since the IGP can take 224MB away from it. 4GB is not really needed "to keep up" if you ask me, more luxury(personal experience)

When you buy more memory, take the DDR2 800MHz (PC6400)or more variant so your chances that it will be compatible with a new mainboard are bigger if you wish to buy one in the near futre.

---

