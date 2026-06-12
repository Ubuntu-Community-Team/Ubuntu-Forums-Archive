---
title: "Some kernel problems..."
date: 2008-12-18
forum: General Help
---

### Post by Crafty Kisses on 2008-12-18
Hey guys I'm very familiar with the Linux kernel, but I'm having this big issue with my sound on Ubuntu 8.04, so much of an issue that I had to recompile the kernel, to make it work. I've searched this on the forums and Google, still nothing. Supposedly it thinks I compiled the kernel with: ```
CONFIG_INPUT_UINPUT
```I'm trying to compile the 2.6.25 kernel. I also ran the following: ```
cat /boot/config-2.6.22-14-generic | grep UINPUT 
```
Just to see if that option even exists with the current config file I'm using, and there doesn't appear to be an option. I obviously got the kernel from [www.kernel.org](www.kernel.org).

---

