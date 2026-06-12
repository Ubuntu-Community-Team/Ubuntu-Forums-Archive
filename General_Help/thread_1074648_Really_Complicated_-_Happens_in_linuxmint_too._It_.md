---
title: "Really Complicated - Happens in linuxmint too. It may or may not happen in Ubuntu."
date: 2009-02-19
forum: General Help
---

### Post by jjpcexpert on 2009-02-19
Solved
I just did a non-full upgrade of Mint, and I ended up trashing my mint4win WUbI system. I am currently posting in Windows Vista as it is my backup system and a recognized drive is a Wubi host..


Here is how my problem started. 
I was doing an upgrade in Synaptic, missing out mintSystem and busybox-initramfs but still upgrading the rest. Now I cannot boot my Linux System. Ok here is how the Crash went.

I started

hp bios

selected ubuntu/linuxmintmain... 

started things, including cmain()

grub prompted esc to enter...

I booted the kernel 2.6.27-11 generic (upgraded kernel) and guess what:

Booting "operating info removed : 2.6.27-11-generic
All this stuff happens:

-----Kernel Panic! not syncing. VFS: cannot mount root fs on unknown block[0,0] (the unknown block was to do with Wubi. It is ok)



Sorry if this hurts the forums but it happens in both of:

x-, k-, normal and ed- Ubuntu
Linux Mint XFCEmint KDEmint FREEmint MAINmint. (and fluxmint aswell)


Someone with lots of coffee beans plz reply! It is sooooo complex.

Adding on LinuxMint 6 Xfce CE where I have the driver problem. If I boot into 2.6.27-7 and then install the new mintSystem or Ubuntu LSB info, I restart into 2.6.27-11 with a working kernel.
:p:KS;):guitar::guitar::popcorn:

---

