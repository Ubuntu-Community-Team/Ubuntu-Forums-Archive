---
title: "Kernel Compile /Library Dependencies"
date: 2005-12-29
forum: Desktop Environments
---

### Post by AntiMattR on 2005-12-29
I am trying to recompile the kernel for my Mini-ITX system running Breezy.  I have been following: [https://wiki.ubuntu.com/ViaEpiaDriHowto](https://wiki.ubuntu.com/ViaEpiaDriHowto) but in the article the author does not go into enough detail about which libraries I need to perform the build.  It just says:

> All packages that is required for building a kernel. "build-essential" and "bin86" at least. You will also need extra packages for the frontend when you build the kernel. Example "libncurses5-dev" is needed for "make menuconfig".

After adding in the packages for countless many libraries ‘make’ always ends up failing because some dependency somewhere isn’t met.

Can someone give me a fairly quick and solid procedure for getting this kernel recompiled?

Thanks a lot!

---

