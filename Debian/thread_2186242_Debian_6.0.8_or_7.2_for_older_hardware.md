---
title: "Debian 6.0.8 or 7.2 for older hardware?"
date: 2013-11-06
forum: Debian
---

### Post by Stevensthunar on 2013-11-06
I decided to install Debian, but i don't know which version.I have old hardware.I tried out dual-booting Xubuntu 12.04 and Debian 7.2. Debian 7 was OK, but sometimes it freezed down completely, and i had to restart the computer.I didn't try out the new 6.0.8 yet. Should i try it?

---

### Post by lykwydchykyn on 2013-11-06
Depends on the hardware, and which software you want to run.  If you run the default desktop (GNOME), then there's a large difference between 6 and 7 because you go from GNOME 2 to GNOME 3.  If you run some other desktop environment (LXDE or XFCE would probably be good) then you won't see as much of a resource difference and would probably be better of with 7.

Just my opinion, but I prefer to run newer versions with lighter software rather than run an older version.

---

### Post by CharlesA on 2013-11-06
I thought Squeeze was going End-Of-Life in about six months or so?
[https://wiki.debian.org/DebianSqueeze/](https://wiki.debian.org/DebianSqueeze/)
[https://wiki.debian.org/DebianOldStable](https://wiki.debian.org/DebianOldStable)

I'd go with Wheezy running XFCE or LXDE, myself.

---

### Post by trent.josephsen on 2013-11-06
As it happens, Jessie (the current testing branch of Debian) recently switched to use Xfce by default. [Reference link.](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=dfca406eb694e0ac00ea04b12fc912237e01c9b5)

I use Xfce on Arch myself, so count this as another vote for newer versions of lighter software. You didn't say exactly how old your hardware is, but if that is still sluggish (doubtful) you may try a still lighter solution like Openbox. (I have a soft spot in my heart for Openbox, but I haven't really used it in years.)

---

### Post by ian-weisser on 2013-11-06
> **Stevensthunar said:**
> Debian 7 was OK, but sometimes it freezed down completely, and i had to restart the computer.

I would figure out why it freezed down.
Video card? That can usually be tweaked or fixed.
Other hardware? Lots of fixes for those available, too.
System resources too low?

---

### Post by BBQdave on 2013-11-07
> **Stevensthunar said:**
> I decided to install Debian, but i don't know which version.I have old hardware.I tried out dual-booting Xubuntu 12.04 and Debian 7.2.

Depending on how old, *old* hardware is... I think you are on the right approach, Xubuntu 12.04 or Debian 7 with Xfce :) 

And adding RAM, if possible, helps system performance.

---

### Post by su:bhatta on 2013-11-16
I use Debian 7.2 but with Gnome it may be a little heavy for your system. 

I would suggest you to try Debian 7.2 with FVWM-Crystal. It is a WM/DE. Installable from Synaptic, and uses minimum resources. 
You can configure it with pre-installed recipes. Looks good and very light. 

Highly customizable too. !

---

