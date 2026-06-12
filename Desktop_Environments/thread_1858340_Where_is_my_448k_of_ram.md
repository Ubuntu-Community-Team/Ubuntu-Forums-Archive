---
title: "Where is my 448k of ram?"
date: 2011-10-12
forum: Desktop Environments
---

### Post by orion188 on 2011-10-12
Hi there.
The story in brief:

- I have a data acquisition card, + an Ubuntu driver for it + 2G of RAM.

- It tries to **directly** access some part of the higher memory. 
By "**directly**" I mean it does not seem to negotiate with the Linux kernel. Such that whenever I did "*insmod xxx.ko*" some strange visual effects appeared on my screen which seems to be a conflict with the Video memory (Also confirmed by the provider company).

- After some investigation, I found out that about 128M of memory is given to my on-board graphics device, BEFORE even the kernel knows about it, such that "*dmesg | grep Memory*" showed approximately (2G - 128M).

- I disabled the onboard graphics device, and used an external one. The problem is **almost** solved. **Almost**, since there's still 448k missing. (This is not a calculation mistake since I've done the calculations all in bytes, not in G or M or k) And this is not what the kernel does, since the kernel "is seeing" only that amount of memory. So something is happening before the kernel is loaded!

I don't know where this part of memory is going, and I can't give this up, since the driver does not ask any one and does what it does, right where it wants!

Thanks in advance for any helps.

---

### Post by Basher101 on 2011-10-12
I got the same. My onboard takes 248 MBs of my total 4 Gigs of RAM. The system monitor always shows "xxx of 3.8 GB RAM". As for your external video card and even more RAM usage,

i have no idea..

---

### Post by orion188 on 2011-10-12
> **Basher101 said:**
> I got the same. My onboard takes 248 MBs of my total 4 Gigs of RAM. The system monitor always shows "xxx of 3.8 GB RAM". As for your external video card and even more RAM usage,

i have no idea..

@Basher101,
Thanks for your reply.
Please run 
```
dmesg | grep Memory
```in a terminal and let us know what it says. (Please take care that "Memory" is exactly typed with capital 'M')

---

### Post by Basher101 on 2011-10-12
```
[    0.000000] Memory: 3965992k/5242880k available (5943k kernel code, 1120340k absent, 156548k reserved, 5015k data, 956k init)
```
thats the output

this does not really tell me anything..what part of the output am i supposed to be looking at?

---

### Post by orion188 on 2011-10-12
@Basher101,
It says you have 5G of ram! (5242880k)
Do you?

---

### Post by Basher101 on 2011-10-12
no i have only 4 GB RAM (2x2 gb modules). I have an eMachines-E725 laptop btw.

---

### Post by orion188 on 2011-10-12
It's strange!
But your problem is different to mine, since your kernel is "seeing" all the available ram (even more!).
But mine shows only 2048M-448k = 2096704k !

Any one? Any ideas?!

---

### Post by Basher101 on 2011-10-12
well i dunno for the kernel, but the system monitor shows just fine

---

### Post by orion188 on 2011-10-12
Bump!

---

### Post by mcduck on 2011-10-13
The kernel itself is loaded into RAM before it can be booted (initial ramdisc), and therefore takes part of it, thus leaving you with a bit less accessible RAM than you have physical RAM available. Linux doesn't count the amount of RAM used by the kernel as available because it never will be, you can't unload the kernel from memory while the OS is running.

So it's perfectly normal that you have a bit less available memory than what's physically installed on the machine. Some programs might just tell you the total amount of RAM as based on the physical RAM modules installed, while others give you more "honest" report, only counting the RAM actually available.

---

### Post by orion188 on 2011-10-15
mcduck,
Thanks for your reply. 
How can I know which part of the physical ram is occupied by the kernel? And which part by other stuff?
Is there any command/program that shows the exact memory mapping (or is "memory mapping" the right term to use at all?)

---

### Post by mcduck on 2011-10-15
> **orion188 said:**
> mcduck,
Thanks for your reply. 
How can I know which part of the physical ram is occupied by the kernel? And which part by other stuff?
Is there any command/program that shows the exact memory mapping (or is "memory mapping" the right term to use at all?)

Pretty easy, run something like "free -m" to get a report of used and available RAM. The difference between physical RAM installed on your machine, and the total amount of available RAM reported to you would be the part where the kernel is loaded during boot.

If there's any way to directly measure this, I'm not aware of it. Could be pretty hard because, like I said, that part of memory is not available or visible to any programs.

Of course that's not all RAM the kernel might be using, only the RAM occupied by the kernel image. Once booted the kernel will use more memory, for example by loading additional modules etc.

(This is of course assuming there are no other limitations to how much memory your system is capable of addressing, like in case of having much RAM installed but not using 64-bit or PAE kernel)

---

