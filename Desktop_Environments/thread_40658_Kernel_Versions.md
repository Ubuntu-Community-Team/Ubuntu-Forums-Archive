---
title: "Kernel Versions?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Phixion on 2005-06-09
Hi there, lately I updated all the packages possible in Ubuntu, when booting up GRUB shows 2 different Kernels, one ending in 686 and another ending in something else (I don't remember now).

Is there any reason its like that? which one should I be running?

Cheers.

---

### Post by codejunkie on 2005-06-09
the i386 and i686 kernels are optimised for intel but will also work on AMD Processors so ubuntu installs the i386 kernel by default to avoid problems with older machines, but the i386 kernel doesn't support 1 gig of ram or more it only see's around 700-900 MB of it. for example if your system is a 700mhz intel with 256mb of ram you only need the i386 kernel because you don't need the support for the extra ram. also if you have an AMD CPU for example AMD Athlon XP 3000+ processor you need to be using the k7 kernel image it's optimised for the AMD processors hope this helps.

---

### Post by gonenowhere on 2005-06-23
where can i find the k7 kernel? actually im having problems it freezes if i have 1 gig of ram but with 512 its cool. is that a kernel issue

---

### Post by TheRealEdwin on 2005-06-23
I run on a ASUS Z71V with the Dothan Pentium M (686 I think). How would I go about removing the 386 kernel. I know how to remove it from grub but I want to uninstall it completly.

---

### Post by spacemonkey on 2005-06-23
wow, that explains a lot.  Thanks.  I've got a P4 2.8 ghz HT, with a gig of ram, and it says I've only got 900MB.  How would I go about installing the i686 kernel, hopefully without screwing up the whole system.

---

### Post by spacemonkey on 2005-06-23
A quick forum search revealed that all I had to do was install via apt or synaptic.  I love debian based distros.  Downloading the new kernel now.

---

### Post by frozen_fire on 2005-06-23
if you have HT you need 686 smp kernel for the HT to work

---

### Post by arunsub on 2005-07-10
[QUOTE=spacemonkey]A quick forum search revealed that all I had to do was install via apt or synaptic.  I love debian based distros.  Downloading the new kernel now.[/QUOTE]
What was your search term in synaptic? I have Athlon 64 2800+. Which kernel is good for that (32 bit, i don't want 64 bit)? What do I search for in synaptic?

---

### Post by valnar on 2005-07-10
[QUOTE=frozen_fire]if you have HT you need 686 smp kernel for the HT to work[/QUOTE]

Except that I wouldn't recommend it.  The HT 686 SMP kernel is buggy, IMO.  I had to go to a single i686 kernel on my dual Xeon.   ](*,) 

-Robert

---

### Post by Joeb on 2005-07-11
[QUOTE=arunsub]What was your search term in synaptic? I have Athlon 64 2800+. Which kernel is good for that (32 bit, i don't want 64 bit)? What do I search for in synaptic?[/QUOTE]

I'm not at my Ubuntu box right now, but you could search for "k7" to see all of the kernels compiled for AMD Athlon CPUs.  You could also just scroll through the list of packages.  I believe the kernels all begin with "linux".

---

