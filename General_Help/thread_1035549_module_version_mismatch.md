---
title: "module version mismatch"
date: 2009-01-09
forum: General Help
---

### Post by pbramji on 2009-01-09
Hello,

In my attempt to get more familiar with the usbnet driver on Linux, I tried writing a sample shell driver that uses the usbnet functions and added a bunch of logging messages.

I downloaded the latest version of Ubuntu, compiled a kernel and loaded my module and it seems to work correctly. The linux kernel version was 2.6.24.21-generic.

I then took my sample code and tried doing the same thing on a different (already installed with Ubuntu) machine in the lab. I found a bunch of errors using dmesg saying: "disagrees with symbol usbnet_suspend". The linux distribution on this machine is custom built with 2.6.24-16-generic for which I do not have the source and possibly cannot obtain it. I ran modinfo usbnet and it says vermagic is 2.6.24-16-generic.

The source I downloaded using Synaptic package manager is linux-source-2.6.24.tar.bz2 which seems to use 2.6.3 as the base version. When I build this code, modinfo shows 2.6.3. I tried changing the EXTRAVERSION in the Makefile prior to compile, but have no luck with that. modinfo on usbnet shows the expected version 2.6.24-16-generic, but the module does not load.

I am new to Ubuntu and dont compltely understand the version numbering scheme. I looked at the kernel/module.c file and it appears that there may be some CRC issue though I am not knowledgeable enough to determine that.

I would appreciate any help in fixing this problem. I just want to be able to compile my shell driver and load the module.

---

