---
title: "Main memory missing..?"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mucho_maze on 2009-01-21
Hey

I have a new Dell inspiron 530 with integrated Intel Graphics Media Accelerator and 4 gb of main memory. When I boot up in either ubuntu or windows it says I've got only 3,3 gb ram. In windows I can see that the Intel GMA has 128 mb memory + 156 mb (main memory) which sums to less than 300 mb.

When I enter the BIOS, it says correctly that 4096 mb memory is installed. Is it really true, that the Intel GMA takes about 700 mb from the main memory? Is there something wrong?

---

### Post by stefangr1 on 2009-01-21
It is very likely that this is due to using a 32-bits operating system. You can check this out by giving the command:

uname -a

If you already have the 64 bits os, it will show something with x86_64. Otherwise you could install the 64-bits version of Ubuntu.

---

### Post by Cannotcompute on 2009-01-21
Yeah, 32-bit OS's cant handle more than ~3.2 GB of ram. Any more than that, unfortunately, cannot be used.

---

### Post by mucho_maze on 2009-01-24
> **Cannotcompute said:**
> Yeah, 32-bit OS's cant handle more than ~3.2 GB of ram. Any more than that, unfortunately, cannot be used.

Thanks for your replies stefangr1 and Cannotcompute. I do have a 32 bit machine, and I was convinced that a 32 bit machine could address 4 gb ram... So you are telling me that it's the 32-bit OS's (both linux and windows) that cannot handle all the memory and not the 32-bit machine itself...?

---

### Post by Secrest on 2009-01-24
> **mucho_maze said:**
> Thanks for your replies stefangr1 and Cannotcompute. I do have a 32 bit machine, and I was convinced that a 32 bit machine could address 4 gb ram... So you are telling me that it's the 32-bit OS's (both linux and windows) that cannot handle all the memory and not the 32-bit machine itself...?

That's right.  It's the 32 bit OS.  It has nothing to do with your machine.  If you installed a 64 bit OS it would use the entire 4 gb of ram or more if you had it.

---

### Post by boof1988 on 2009-01-24
Check out [this thread](http://ubuntuforums.org/showthread.php?t=855511).  Step *2.1)* may be of use to you.  It says how to install the server kernel (which is pae enabled), so it should allow access/use of all your RAM.

HTH...

---

### Post by bd_thompson on 2009-01-24
> **Secrest said:**
> That's right.  It's the 32 bit OS.  It has nothing to do with your machine.  If you installed a 64 bit OS it would use the entire 4 gb of ram or more if you had it.

Not mentioned is an addressing issue.  

Even if your video has inbuilt memory, the system must map it into main memory addresses.  So, if you have a 512mb video card, 512 mb of main memory becomes unusable because the video memory is using the addresses. This does NOT mean the video processing is happening in main memory.  Those addresses become idle.  

What's the advantage you say?  On board video memory can respond much faster than main memory to the GPU. 

Dave Thompson

---

### Post by Aintaer on 2009-04-16
I seem to have a similar situation on my new XPS M1530.  The system has 4GB physical RAM, and has 256MB VRAM.  However, 512MB is "missing" and NVIDIA's driver reports having 512MB VRAM.  I am running on 32-bit Hardy.

How can I make sure that the GPU is using its dedicated VRAM instead of going on the system RAM?

---

