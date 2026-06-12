---
title: "KDE4 slow on quite fast laptop!?"
date: 2010-02-20
forum: Desktop Environments
---

### Post by Markus72 on 2010-02-20
Hi folx,

I'm not sure how to name it - it's strange.
I use Kubuntu 9.10 and face the fact that the KDE4 desktop effects on my wife's laptop look much more smooth than on mine.

My wife's laptop: Intel Centrino 1.73GHz, 1GB RAM, Intel GMA 900 (5 years old)

My laptop: Intel Core 2 Duo about 2,7GHz, Intel GMA 4500HD (0,5 years old)

Yes, my desktop resolution is somewhat higher but that cannot be the reason.

On both machines, comparable desktop effects are enabled including shadows and transparency.

I just updated to KDE 4.4, hoping to get rid of choppy animations, but I had no luck.

Any idea? I hate my wife mocking me with that :D

Markus

---

### Post by warp99 on 2010-02-20
Here's the reason why:

>  Intel GMA 4500HD

Another thread with similiar issues:

[http://ubuntuforums.org/showthread.php?p=8771334](http://ubuntuforums.org/showthread.php?p=8771334)

It's the Intel drivers for that particular chipset. You can install Kernel Mode Setting (KMS) as one of the posts suggest:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Just scroll down for Intel cards and follow the instructions, it's not very difficult. BTW this should be fixed in Lucid (10.4) if you prefer to just upgrade in about a month or so.

---

### Post by moe_syzlak on 2010-04-01
> **Markus72 said:**
> Hi folx,

I'm not sure how to name it - it's strange.
I use Kubuntu 9.10 and face the fact that the KDE4 desktop effects on my wife's laptop look much more smooth than on mine.

My wife's laptop: Intel Centrino 1.73GHz, 1GB RAM, Intel GMA 900 (5 years old)

My laptop: Intel Core 2 Duo about 2,7GHz, Intel GMA 4500HD (0,5 years old)

Yes, my desktop resolution is somewhat higher but that cannot be the reason.

On both machines, comparable desktop effects are enabled including shadows and transparency.

I just updated to KDE 4.4, hoping to get rid of choppy animations, but I had no luck.

Any idea? I hate my wife mocking me with that :D

Markus



Kubuntu is a neglected animal. Try out a different distro with KDE. The Ubuntu devs only care about GNOME stuff, thus KDE is left neglected and you have a slow KDe/kUBUNTU. Try out OpenSUSE. I'm running all snappy on my netbook.

---

### Post by Silent Warrior on 2010-04-01
I'm also running an Intel 4500 (in Mint 8 - must be the same drivers/kernel that ships with Ubuntu), and I feel KDE is pretty responsive... Have you checked the CPU frequency governing? If you're set to conserve power - well, need I say any more? (Flash in Firefox is considerably more sluggish than it is in Gnome, though, I'll readily admit that.)

---

