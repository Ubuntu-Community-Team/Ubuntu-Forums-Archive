---
title: "Question about installing Nvidia video card driver?"
date: 2006-04-29
forum: Desktop Environments
---

### Post by tommcd on 2006-04-29
I have nvidia 6200 video card. On the Ubuntu wiki:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
it says to install via synaptic:
1)nvidia-settings
2)nvidia-glx
3)then it says to search for "linux-restricted-modules" and install linux-restricted-modules-386, or linux-restricted-modules-686 linux-restricted-modules-k7 if you are running the 686 or k7 kernel.
I was a bit confused about the last part. So far I installed #1 and #2. I enabled the driver (sudo nvidia-glx-config enable) and I get the nvidia splash screen on boot up and I can get nvidia settings. Everything seems ok.
Question: do I need the 'linux-restricted-modules? and if so, which ones of #3? I am on Ubuntu 5.10 Any advice appreciated, thanks!

---

### Post by bluevoodoo1 on 2006-04-29
if you open a terminal and type... uname -r your kernel will be displayed. For example, for me it gives 2.6.15-21-686. So I would use the linux-restricted-modules-686.

But if the nvidia splash screen is coming up... hmm. Perhaps it's working?

what does the output of 'glxinfo' look like?

---

### Post by DoktorSeven on 2006-04-29
In my experience the linux-restricted-modules package was already installed when I installed/did the initial update of Breezy.  

Search for it in Synaptic and see if it's already installed.  If so, you're set.

---

### Post by tommcd on 2006-04-29
Thanks guys. When I type uname-r I get: 2.6.12- 10- 386. 
If I search for linux-restricted-modules in synaptic, several of them are already installed, including one numbered -386 followed by: 2.6.12.16.1. Is that the right one? Am I ok?
The output of glxinfo:
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:...followed by a LOT of gibberish! Is that good? Thanks guys!

---

