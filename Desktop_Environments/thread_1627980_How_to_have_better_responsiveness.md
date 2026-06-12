---
title: "How to have better responsiveness?"
date: 2010-11-22
forum: Desktop Environments
---

### Post by uqbar on 2010-11-22
Hi all.
I'm running Kubuntu 10.10 and am struggling to have a more responsive system.
It's a laptop with 4GB ram, a T9500 CPU (amd64) and a 7200 rpm SATA disk, so there should be plenty of horsepower to have a decent non-server system.
I'm not using any eye candy like 3D desktop and the likes.
What happens is that with higher workloads like massive file copy (not only over USB disks) or even DVD burning I am not able to use a text editor (vi in my case) in a decent way until the workload finishes.
I have understood that the so-called "generic" kernel I'm using (2.6.35-23-generic) is not well-suitable for desktop usage but rather for servers as fas as responsiveness is concerned.
Well, I could compile the latest kernel by myself but I fear I could break something up without the needed patches and current kernel configuration options.
I've seen also the ppa:kernel-ppa/ppa but it's (oddly) geared to Lucid only.
What could then be a solution in your opinion?

---

### Post by Spice Weasel on 2010-11-22
KDE isn't very fast - you should try a more lightweight GUI like LXDE, Enlightenment or Openbox.

---

### Post by koleoptero on 2010-11-22
That system should be fast enough for KDE with full bling.

It's all about how your system manages these resources. Did any other operating system have a similar problem with high loads? Also, sometimes the system temperature has a lot to do with it. In my laptop if the CPU gets too hot ACPI drops its cycles to the minimum.

I've had similar problems with KDE, it's not very efficient unfortunately (imho) but try disabling some things like compositing. Also install htop (sudo apt-get install htop) and check from it to see if perhaps the ram is full with cache and buffers. KDE would do that to me sometimes. But your 4 gigs of RAM should be OK.

P.S.: consider compiling your own kernel only as a last resort. Kernel bugs can be catastrophic.

---

