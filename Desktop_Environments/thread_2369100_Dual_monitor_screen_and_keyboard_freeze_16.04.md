---
title: "Dual monitor screen and keyboard freeze 16.04"
date: 2017-08-18
forum: Desktop Environments
---

### Post by Robbyx on 2017-08-18
I have an AMD CPU. My screen and keyboard keeps freezing. I have to  wait a few minutes and it comes to life again. 

I found a possible  solution to the keyboard and monitor screens freezing suggested at 

[https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly#796484](https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly#796484)

```

There is a line in that: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (like this), replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
```

What default wording should I use for:

AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G × 4 
Gallium 0.4 on AMD KAVERI (DRM 2.49.0 / 4.10.0-32-generic, LLVM 4.0.0)

Robin

---

