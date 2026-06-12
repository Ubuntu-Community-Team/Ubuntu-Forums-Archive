---
title: "Newer kernel -&gt; recompiling?"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-19
I have one driver installed that I've compiled from source (spca5xx).
Two days ago I installed kernel updates through apt-get update and I had to recompile the driver, my system hang everytime I tried to use my webcam.
Now was I wondering, do you have to recompile everything when you update your kernel? That could take pretty long when you've installed more apps from source..
Or is there a way around it?

---

### Post by claes on 2006-02-19
You don't need to recompile everything. You only need to recompile the driver module spca5xx for the new kernel. Linux kernel is not ABI compatible between versions so a new kernel version you have to recompile driver modules.

The Linux kernel will never have static ABI for drivers so no need to start this discussion. Linus Torvalds said a big no to this. He want's the hardware vendors to open source the drivers and he will include them in the mainstream kernel and the problem is solved. 

Claes

---

### Post by Ramses de Norre on 2006-02-19
What's ABI? And if I understand you right, you have to recompile driver modules but not other applications?

---

### Post by claes on 2006-02-19
[QUOTE=Ramses de Norre]What's ABI? And if I understand you right, you have to recompile driver modules but not other applications?[/QUOTE]

That's correct you only need to recompile the driver module not any applications.

ABI stands for Application Binary Interface it's the way a binary program like driver modules communicate with binary libraries like the linux kernel. 

API stands for Application Programmable Interface. The difference is that API is if the source code is compatible between different versions and ABI if the binary (compiled) version is compatible. 

The linux kernel is mostly API compatible but never ABI compatible. That means that you have to recompile your modules if you switch kernel. But mostly you don't have to get a updated source version as it's API compatible. 

Hope I could explain this.

Claes

---

