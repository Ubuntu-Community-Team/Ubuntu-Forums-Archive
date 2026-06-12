---
title: "n00b concept help: restricted modules"
date: 2005-12-14
forum: General Help
---

### Post by nelposto on 2005-12-14
Hey people,

10 days of linux and counting.. it's been pretty cool so far.

Working with custom kernels here, and I'm aware of the problem with restricted modules. However I don't fully understand the issue.

Trying to compile the modules into the kernel for me has been a less than successful experience, so I'm trying to understand if compiling the modules into the kernel is the only solution.

Specifically, I'm working with fglrx for my ATI graphics card, and ndiswrapper for my wireless.

What's to stop me from compiling the kernel, and then installing the drivers? Isn't this the same thing as what I did when I was using kernel xxxxxxx.12? (Given that I'm now working with xxxxxxxx.14). I tried installing the proprietry ati drivers in my new kernel, and while it _seemed_ to work alright (fglrxinfo yields correct results), tuxracer wont run, describing a missing GLX visual... wootever that might be.

Any stabs at an explanation would be much appreciated..

---

### Post by mikkelwe on 2005-12-14
You gotta make sure the module is loaded (lsmod) and that X is using it (edit xorg.conf).
Read the ATI wiki on wiki.ubuntu.com if you didn't already do so. Also of course the precompiled modules in the repos will only work with the kernels they're compiled for, eg *not* your custom kernel.

---

