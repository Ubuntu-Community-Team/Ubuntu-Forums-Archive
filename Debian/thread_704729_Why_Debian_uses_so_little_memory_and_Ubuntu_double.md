---
title: "Why Debian uses so little memory and Ubuntu double?"
date: 2008-02-22
forum: Debian
---

### Post by KOTAPAKA on 2008-02-22
Hello I installed Debian yesterday and when I checked the memory usage it was about 81MB!!! I said WOW this thing can run on any machine. I installed Ubuntu today and a freshly installed Ubuntu eats about 180 -200MB that is more than double. Why? What is the difference? I mean Debian has similar configuration - GNOME, nautilus, and a lot of stuff Ubuntu uses (well it uses Firefox instead of what Debian has). I mean Debian runs soooo smoothly. Note that both had the same number of panels - actually just sound on/off and Networks.

---

### Post by Crooksey on 2008-02-22
Ubuntu dosent use pure gnome, its patched with other stuff and stuffed full of depedncies, so it loads more than you actually require.

---

### Post by justin whitaker on 2008-02-22
It's the special sauce. All those modifications, dependencies, and usability hacks that make Ubuntu so cool are a performance hit in the RAM department. 

You can, of course, strip all that out and load vanilla Gnome and get real close to Debian's RAM usage.

---

### Post by kerry_s on 2008-02-22
debian's built with the old stuff in mind. debian knows there stuff will not always be run on the state of the art stuff. they have been at it far longer than ubuntu and have already learned from previous mistakes.

ubuntu drops support for older hardware, doesn't bother with optimization of anything, modifys and tweaks it till it fits the ubuntu way, no matter how badly done. ubuntu doesn't care what you try and run it on, but has set minimum requirements.

my start up ram on debian is 17.6mb, climbs from there with use, drops back down to around 20mb's with everything closed and idle.
i run debian custom install on 450mhz 256ram

---

### Post by cprofitt on 2008-02-22
> **KOTAPAKA said:**
> Hello I installed Debian yesterday and when I checked the memory usage it was about 81MB!!! I said WOW this thing can run on any machine. I installed Ubuntu today and a freshly installed Ubuntu eats about 180 -200MB that is more than double. Why? What is the difference? I mean Debian has similar configuration - GNOME, nautilus, and a lot of stuff Ubuntu uses (well it uses Firefox instead of what Debian has). I mean Debian runs soooo smoothly. Note that both had the same number of panels - actually just sound on/off and Networks.
 
 
Debian installed two browsers... once of which is Iceweasel and that is really Firefox w/o the copyright protected images and name. The other browser (Epiphany) is not bad, but I prefer Iceweasel.

---

### Post by mivo on 2008-02-23
Ubuntu is designed to be complete out of the box, so there may be some "services" running that you may not be needing. Just go to *System -> Preferences - Sessions*, and uncheck in the "Startup Programs" tab what you don't need. (Be sure you don't need it, though.)

---

### Post by K.Mandla on 2008-02-23
Moved to Debian subforum.

---

### Post by tdrusk on 2008-02-23
I always thought it would be cool to take Debian unstable and put all the packages that ubuntu has on it so it's exactly like Ubuntu with rolling updates and such.

---

### Post by tgalati4 on 2008-02-23
Those crazy folks at Linux Mint discovered the same thing.  They built a version of Linux Mint based on pure Debian to see what the performance would be.  This was a test case, not sure if they will support it or continue to build pure Debian versions going forward.

If you have the talent to build a pure Debian system and set it up the way you want, then you have created your own personal distribution.  Ubuntu is casting a wide net, but takes a performance hit in the process.

---

### Post by Antman on 2008-02-23
> **tdrusk said:**
> I always thought it would be cool to take Debian unstable and put all the packages that ubuntu has on it so it's exactly like Ubuntu with rolling updates and such.

I'm addicted to sid's rolling release nature; I use it in the form of Sidux.

---

### Post by ubuntu-freak on 2008-02-23
> **KOTAPAKA said:**
> Hello I installed Debian yesterday and when I checked the memory usage it was about 81MB!!! I said WOW this thing can run on any machine. I installed Ubuntu today and a freshly installed Ubuntu eats about 180 -200MB that is more than double. Why? What is the difference? I mean Debian has similar configuration - GNOME, nautilus, and a lot of stuff Ubuntu uses (well it uses Firefox instead of what Debian has). I mean Debian runs soooo smoothly. Note that both had the same number of panels - actually just sound on/off and Networks.

 
What's the RAM usage like if you disable desktop effects and reboot? 
 
Nathan

---

### Post by tommcd on 2008-02-24
I have installed both Ubuntu and Debian on 3 desktop PCs and a laptop. The Ubuntu installs were all default desktop installs and the Debian installs were all from the 1st Debian install CD, no net installs. On each system Debian ran much faster and used fewer resources than Ubuntu.
The beginner friendliness of Ubuntu comes with a significant performance penalty.

---

### Post by tdrusk on 2008-02-24
I just installed Debian on my laptop after installing it on my slow Desktop. I installed the default Gnome desktop. It literally runs as fast as Xubuntu.

---

### Post by deepclutch on 2008-02-25
I am on Debian Sid for the past 2 years-upgrading,overwriting,bug reporting and overall enjoying the Sid experience .
BTW,I have Debian Sid apt-pinned with lenny and experimental repository(for upstart-I use upstart on Debian!).

Debian is always faster and I am on 95% on my Debian Sid,while I do boot into ubuntu once in a while :p

Debian with firefox3beta4 which I use is currently using 217MB of RAM on a prescott 2.8Ghz HT machine ;) yes,blame it on firefox and proprietary nvidia driver(may be!) for this much RAM use! :-|

---

