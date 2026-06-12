---
title: "Latest kernel update caused panic mode (hardy)"
date: 2009-05-09
forum: General Help
---

### Post by trikster_x on 2009-05-09
I got the update for the latest kernel - Ubuntu 8.04.2, kernel 2.6.24-24-generic  - a few days ago and it puts me in a kernel panic mode when I start my computer.  When I installed it asked me what I wanted to do with /boot/grub/menu.lst because I had changed the contents of the file locally.  I chose to allow the installation to change the file rather than keep it the same since I had this exact same problem on another computer when I kept my settings.  I ended up removing the update without thinking twice on my other comp, but I would like to keep this comp on the most up to date kernel.  I am using an Aspire One with 120GB HDD and 1.5GB RAM.  Is there a problem with the newest kernel and my hardware?  Or did I do something wrong

---

### Post by trikster_x on 2009-05-09
A little help here...

---

### Post by paradigm2 on 2009-05-09
> **trikster_x said:**
> A little help here...

When it gave you the kernel panic, did it give you any more information such as something like:

"VFS: Unable to mount root device"

?

---

### Post by trikster_x on 2009-05-10
What it displays changes every time I boot up.  Sometimes it will give me a bunch of memory addresses, sometimes it will start naming a couple modules.  Once in a while there will be no text displayed at all, it will just crash.  I will reboot later today and post whatever text I get.

---

### Post by trikster_x on 2009-05-11
Okay, I rebooted a couple times and got two different sets of text.  The first time I got:
```
Starting up ...
[13.727492] PANIC : double fault, gdt at c1bfa000 [255 bytes]
[13.727546] double fault , tss at c1bfd100
[13.727590] eip = c01055fb , esp = bcc900c1
[13.727636] eax = 120bc000 , ebx = c0120cbf , ecx = 00000000 , edx = f7c6be68
[13.727687] esi = 00000000 , edi = f7c65f68
[13.731187] BUG : unable to handle kernel NULL pointer deference at virtual address 00000000
[13.731277] printing eip : c01054a0 *pde = 00000000
[13.731393] PANIC : double fault , gdt at c1c06100
[13.731442] double fault , tss at c1c06100
[13.731486] eip = c0105d7b , esp = bcd420c1
[13.731533] eax = c03a087f , ebx = 00000000 , ecx = 00000002 , edx = f7c6bf58
[13.731585] esi = 0047f000 , edi = f7c6bf58
```

The second time I rebooted, I got entirely different text that ended with:
```
Kernel panic - not syncing: Attempted to kill init!
``` 

Anyone who can tell me what's up, or do I need to write down as much of the second set of text as possible?

---

### Post by trikster_x on 2009-05-14
I tried completely removing and reinstalling the 2.6.24-24 kernel through synaptic, but that didn't work.  I still got the same kernel panic message.  I have the kernel completely removed now so I don't have to remember to choose a different kernel from now on.  If anyone out there can help me, I would like to be able to install the kernel and fix it.

---

