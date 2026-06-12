---
title: "Upgrade to new kernel?"
date: 2008-12-30
forum: General Help
---

### Post by Felix_Akasaka on 2008-12-30
I heard that a new kernel came out 2.6.28. How do I upgrade from 2.6.27-7 generic? Should I even?

I'm using intrepid ibex and an AMD Turion64 x2 in 32bit. (I just found out that my processor can run 32 and 64bit. (Odd)

Thank you.

---

### Post by ushimitsudoki on 2008-12-31
Wait for it to come in the normal updates (if it does). Unless you are having a problem that is specifically resolved in a new or different kernel it's better to stick with the one packaged with Ubuntu.

---

### Post by sdennie on 2008-12-31
You would have to build it yourself or upgrade to Jaunty (which is not recommended at this stage of development).  If you are looking for a guide on building your own kernel, this one looks good: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Felix_Akasaka on 2008-12-31
Thanks. I'll just wait for it then.

---

### Post by ToshibaLaptoplinux on 2009-01-05
I am glad I found this thread!

I compiled the new kernel for my Toshiba Laptop (Which has notorious problems with Ubuntu) and there are all sorts of problems that I have encountered. ie: No Sound, wireless, etc

However, it fixed the Shutdown, Sleep, and Hibernate problems I have had since Feisty and...

...my laptop is SCREAMING FAST now. The performance bump is incredible and I am curious if it is because I compiled the kernel for my specific processor (Intel Celeron M; 360J)?

So my question is this: To get the newer kernels in the normal upgrades does one have to go through the Ubuntu upgrades as well? ie: Feisty, Gutsy, Hardy, Ibex etc or I can I keep the version that works best for me ie Hardy and the new Kernel will still come down in the normal updates? ie Running Hardy with the new .28 Kernel.

My dilemma is this...EVERY TIME I upgrade Ubuntu all sorts of stuff breaks. I finally have a fairly well functioning version (Hardy) that has some problems I can live with but would be willing to, once again, spend immense amounts of time tweaking , again, for this bump in performance I am seeing.

Is it possible to recompile the Hardy Kernel with th eonly changed variable being the one for my specific processor instead of the generic?

Sorry if this is a newb question but it is my first compile.

---

### Post by sdennie on 2009-01-05
> **ToshibaLaptoplinux said:**
> 
Is it possible to recompile the Hardy Kernel with th eonly changed variable being the one for my specific processor instead of the generic?


Yes, you can get the Hardy patched kernel source here: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-source-2.6.24_2.6.24-22.45_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-source-2.6.24_2.6.24-22.45_all.deb).  Installing it should create /usr/src/linux-source and it can be built just like any other kernel (at least if you use make-kpkg).  You should be able to install and build that kernel on any version of Ubuntu.

---

