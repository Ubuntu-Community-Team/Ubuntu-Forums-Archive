---
title: "Several critical problems in Jaunty 9.04"
date: 2009-04-21
forum: General Help
---

### Post by keebus on 2009-04-21
Hello community...

...this is quite one of my first posts her (if not the first one), and I apologize in advance for any english mistake.

I've been using Ubuntu for almost 4 years now, my last working release was Hardy. For some time now I'm facing some disappointing problems with the latest releases. With the 8.10 release I was continuously having a kernel panic which I couldn't solve by myself, so I just decided to wait for the new Jaunty.

But again, I'm facing quite many annoying problems. It installs fine, but once GNOME has started:
* Firefox runs extremely slowly, showing blank pages for a while in a complete frozen state. After some time I can see the page, but the application still runs very slowly and it's very little responsive.
* SUDO commands take a long time to be executed.
* Internet is very slow, both with firefox and apt-get.
* Can't install NVIDIA drivers properly, so X doesn't start after the reboot.
* Still, but much more rarely than with 8.10, my keyboard lights start blinking and it freezes completely (kernel panic)

I think these clues are linked some way to the same problem. I would very much appriciate any hint, since I use ubuntu intensively.

Here's my PC configuration:
* Intel Dual Core 2 Duo 6700
* Motherboard: ASUS P5N32-SLI
* 2 GB DDR2 RAM
* 2x nVidia GeForce 7900 GTX in SLi
* nVidia Ethernet Controller for internet

I guess these infos are sufficient. 

Thanks for your kind help and support ubunteros.

Max

**UPDATE**
I finally managed to solve all my problems by upgrading to the newer version of the kernel 2.6.29, that finally fixed those critical bugs.

If anyone interested, just surf to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29"), and you'll find all the debs you need to upgrade your kernel.

Thanks anyway.

---

### Post by Atolla on 2009-05-05
Did this solve the slow internet problem?
My internet is really slow on Jaunty in that there's a lot of latency, while wifi vista is doing fine.

---

### Post by BC4Liberty on 2009-05-07
I woke up this morning to turn on my computer and start my ubuntu 9.04. As it booted up it got almost to the launch screen and just crashed saying "Kernel Panic" and a bunch of other numbers. My caps lock and scroll lock lights flash repetitively. Can some one help me out?

---

