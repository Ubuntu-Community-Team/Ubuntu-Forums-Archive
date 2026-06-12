---
title: "KDE 4.0.1 performance (with composite)"
date: 2008-02-21
forum: Desktop Environments
---

### Post by Captain_Redbeard on 2008-02-21
Hey guys. I'd like to hear what kind of performance you get out of KDE 4.0.1 runnign composite and some desktop effects.

For me it is basicaly unusable due to Xorg chewing away at between 20-75% CPU power from one of my cores, on top of this kwin takes some 20-50% which basically renders the machine heavily bogged down.
it also swallows some hefty 500-600MB RAM.
My setup is:

intel core duo 2 @ 2Ghz
4GB RAM
Nvidia quadro 512MB mem

Imo this should be more than enough to urn an opengl accelerated desktop but apparently not. Am I the only one experiencing this, or maybe some of you have been experiencing similar extremes.

Cheers
/Redbeard

---

### Post by gdzsi on 2008-02-23
i don't have kde4, but compiz-fusion worked flawlessly out of the box with the default gnome desktop of gutsy.  I have an 1,73 Ghz celeron m and intel integrated video card...

do you have the proper nvidia drivers installed?

---

### Post by fracturedmorals on 2008-02-23
> **Captain_Redbeard said:**
> Hey guys. I'd like to hear what kind of performance you get out of KDE 4.0.1 runnign composite and some desktop effects.

For me it is basicaly unusable due to Xorg chewing away at between 20-75% CPU power from one of my cores, on top of this kwin takes some 20-50% which basically renders the machine heavily bogged down.
it also swallows some hefty 500-600MB RAM.
My setup is:

intel core duo 2 @ 2Ghz
4GB RAM
Nvidia quadro 512MB mem

Imo this should be more than enough to urn an opengl accelerated desktop but apparently not. Am I the only one experiencing this, or maybe some of you have been experiencing similar extremes.

Cheers
/Redbeard

<rant = "Rant about KDE4">
You're not the only one man. KDE4 is buggy as hell and, despite all the hype and the pretty looks; NOT release quality.

I've tried several optimizations in my xorg.conf and in my kwin composite settings and have only gotten jerky performance at best.

I'm running with:
AMD Athlon 64 x2 (32-bit ubuntu)
2GB DDR ram
nVidia GeForce 8600 GT (512 Mb ram)

and I'm still getting nothing impressive out of KDE4. Hell....I can play Enemy Territory Quake Wars at full resolution on this system without a hitch, but I can't run KDE4 on a daily use sort of basis.

I'd stick with GNOME/Compiz Fusion, until KDE4 matures a bit more. There's really no advantage to running it right now anyways (Unless you want to try and be useful and report bugs.)

Anyways.
</rant>

---

### Post by Asraniel on 2008-02-23
don't worry people.
Kde 4.0 was never meant to be used as the primary desktop, 4.1 will be for that (well, probably 4.1.1 or something like that).
The current developement version of kde 4 has very much improved, specialy because of the release of kde 4.0, which was perhaps not finished, but helped to get bugreports and testing on all kind of hardware.

---

### Post by fracturedmorals on 2008-02-23
> **Asraniel said:**
> don't worry people.
Kde 4.0 was never meant to be used as the primary desktop, 4.1 will be for that (well, probably 4.1.1 or something like that).
The current developement version of kde 4 has very much improved, specialy because of the release of kde 4.0, which was perhaps not finished, but helped to get bugreports and testing on all kind of hardware.

Good point. I guess the KDE dev team has enough momentum behind KDE3 to live though a full point zero release and receive only complaints and pessimism.

Example:
I can not STAND the konqueror bug in the current kubuntu packages. It just annoys me....I haven't found any real instructions on how to fix it....and launchpad says the bug is solved....when (Considering konqueror still asks me how I want to open links) it's obviously not.

---

### Post by RabidDawgr on 2008-02-24
For people with nvidia 8xxx cards KDE4 performance will suck as these cards are really bad at xrender. QT4 uses xrender extensively so sluggishness will come with that (hell, even gtk apps are much more slow in my 8600 gt than my 6200 which I find ridiculous on NVIDIA's part), Compiz in general sucks on new NVIDIA cards as well.

 Note that also I found kubuntu kde4 packages to be much more buggy and slow than opensuse ones.

---

### Post by Kubunteando on 2008-02-24
RabidDawgr, that very well could be. Can you explain a bit more on xrender and Nvidia 8XXX? Is it a xrender issue or is it really an issue with those Nvidia cards?

I am running KDE 4.0.1 in daily basis with ok performance and I run it with a Pentium M 2GHz, 1GB RAM and ATI Mobility Radeon 9000. This hardware is 3 years old already.
I can do everything nicely. But of course KDE 3.5.8 is faster and smoother.

I have problems with Xorg getting 40% of the CPU continuously  after a few hours of running well. This was a bug in 4.0, supposedly fixed in 4.0.1, but it is there still...

The most annoying bug is that Xorg will crash completely some times, and you loose your session. I haven't notice it follows any particular pattern, this far happens randomly. I was suspecting of the radeon driver, but...

---

### Post by Kubunteando on 2008-02-24
Also I found this:

[http://www.phoronix.com/scan.php?page=article&item=934&num=3](http://www.phoronix.com/scan.php?page=article&item=934&num=3)

So something to check is the driver version.
It seems nvidia, is still finetunning the Linux driver...

---

### Post by RabidDawgr on 2008-02-24
> **Kubunteando said:**
>  Can you explain a bit more on xrender and Nvidia 8XXX? Is it a xrender issue or is it really an issue with those Nvidia cards?

I am running KDE 4.0.1 in daily basis with ok performance and I run it with a Pentium M 2GHz, 1GB RAM and ATI Mobility Radeon 9000. This hardware is 3 years old already.
I can do everything nicely. But of course KDE 3.5.8 is faster and smoother.


if you look at this post:
[performance-and-qt-44]("http://nowwhatthe.blogspot.com/2007/12/performance-and-qt-44.html")

This guy is running arch linux and is getting sluggish resizing etc even with kde 4 and latest nvidia drivers (yes they did improve xrender in 169.04) but apparently in qt4 (4.3 and 4.4 beta) everything seems slow. Its not the new oxygen engine, and people with intel itegrated gfx seem to have completly acceptable speeds. I haven't found any specific clarification as to where the poor perfomance is coming from and in that post a clear reason wasn't found either. 

The sheer fact that an intel gpu works well seems to place the blame at nvidia. Running xrenderbenchmark showed me that only some xrender functions are accelerated and others just left to the cpu. Also note that kde performed better running in xephyr (also true for many others), when the opposite should be the case. 

 PowerMizer also creates problems due to the fact that it does not react to xrender loads (which use the 3d engine of the gpu to accelerate some functions) so it stays in the lowest performance bracket. This also causes problems with compiz (especially the memory clock). 

This doesn't really answer the question and I haven't found any solutions to any of these  problems (workaround for powermizer is to disable it).

p.s. Nvidia is constantly fine tuning the drivers, but I'll be patient and wait till 4.1 to see if these issues get fixed

---

