---
title: "Ubuntu 32 or 64 bit: What is the difference?"
date: 2010-11-30
forum: Education &amp; Science
---

### Post by RichardBrown on 2010-11-30
A few days ago I asked which Linux operating system is the easiest to use, and it sounds like Ubuntu is the one to run. 

Anyhow, I am unsure as to whether I should use the 32 or 64 bit version. I have an AMD 64 bit processor, and I did a bit of Googling to try and figure out which one to install, but the information is conflicting. 

Some websites say that 32 bit is faster for everything except video editing and advanced scientific math calculations, and that 32 bit has less problems with compatibility. Other websites say that 64 bit is faster at everything, and that software compatibility is not much of an issue anymore. 

Which should I install? What are the differences between 32 and 64 bit systems? 

I have an AMD Athlon 3000+ 64 bit processor, and 1 gig of ram.

---

### Post by gunksta on 2010-11-30
You marked this thread as solved, but it seems like you have a question.

Here's the simple answer - 64-bit operating systems are not "faster". They have access to more memory address space, which lets them put more stuff in RAM. To be more specific - 32-bit operating systems can not use more than ~3 Gigs of RAM (main+video). Thus, if you run a computer with 4 Gigs of RAM and have a 32-bit OS on it, some of your RAM will remain unused. 

There are some hacks to get around the memory limitations of 32-bit operating systems but they are beyond the scope of your question because they really don't matter for you.

There are some downsides to running a 64-bit operating system. Some proprietary apps, like Flash are not released or are less stable in their 64-bit incarnations. 64-bit Flash is a beta, but many people use it successfully. FLOSS applications don't generally have a problem running on a 64-bit system. Most stuff was ported a long time ago. 64-bit compiled applications are also slightly larger and actually take up slightly more RAM than their 32-bit counterparts.

You said your system has 1 Gig of RAM. That fact alone makes this easy. On a machine with that little RAM there is absolutely no benefit to running a 64-bit operating system. I run 64-bit on my server and laptop (6 Gigs) but on my netbook (1 Gig) I run 32-bit. It's not an either or, it's choosing the one that is most appropriate for the hardware.

---

