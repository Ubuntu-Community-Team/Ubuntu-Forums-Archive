---
title: "Custom Kernel - Quick Question"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Shigun on 2006-07-18
Ok, i've done the Gentoo install many times before, installing custom kernels from scratch specialized for the specific system.  Now, in an effort to try and fix issues with my computer, Ubuntu, and random hard freezes, im looking to compile a kernel.  I have a quick question though.  All of these modules installed in, do they adversely affect performance?  Is it of any advantage to me, to remove the modules, and compile in the drivers needed for my system alone?

---

### Post by philippe_carlo on 2006-07-18
Modules are not a problem, usually. If they are not loaded, all they do is take up space. However, there are quite a bit of features that cannot be compiled as a module and are available in the standard ubuntu kernels. They bloat your kernel. You will not get a tremendous performance speedup from removing them, though.

---

