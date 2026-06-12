---
title: "is gnome in ubuntu working slower than in other distributions?"
date: 2008-03-16
forum: Desktop Environments
---

### Post by syms on 2008-03-16
hi,
i hear here that many people say that gnome in ubuntu working slower than in other distros, is this true? maybe somebody have tried to run gnome in other distros? thanks.

---

### Post by Lord Illidan on 2008-03-16
Gnome might be slower in Ubuntu because some programs are loaded by default, like Tracker, while in other distros, they might not. I tried a full release of Gnome on Arch Linux (with a mega load of apps) and it didn't feel too different from Ubuntu.

---

### Post by GTvulse on 2008-03-16
I tested Foresight Linux 2.0 yesteday as it already includes Gnome 2.22.0 and it felt slower than Ubuntu 8.04 will be, becasue FL uses Beagle for indexing. Tracker has received a good amount of attention. It is faster and consumes less CPU and disk resources in Gnome 2.22.

---

### Post by syms on 2008-03-16
thanks. so i guess this is not true that gnome in ubuntu is slower than in other distros.

---

### Post by Wyld on 2008-03-16
Is there a list of these things that a problems by default?

Perhaps hiding in the wiki somewhere?

---

### Post by dbera on 2008-03-16
> **dradul said:**
> I tested Foresight Linux 2.0 yesteday as it already includes Gnome 2.22.0 and it felt slower than Ubuntu 8.04 will be, becasue FL uses Beagle for indexing. Tracker has received a good amount of attention. It is faster and consumes less CPU and disk resources in Gnome 2.22.

I would test this theory better before leaning on it. You might want to disable/uninstall beagle in FL and then test gnome speed in FL. I doubt you will see much difference. At least I havent seen much speed difference in Ubuntu (gnome vs gnome w/out desktop search).

---

### Post by GTvulse on 2008-03-17
> **dbera said:**
> I would test this theory better before leaning on it. You might want to disable/uninstall beagle in FL and then test gnome speed in FL. I doubt you will see much difference. At least I havent seen much speed difference in Ubuntu (gnome vs gnome w/out desktop search).

I'm operating under the asumptions of a normal user, which by definition you are not as you do know that disabling Beagle speeds up the system. In fact, the Ubuntu Technical Council decided last week to disable automatic indexing in tracker for 8.04's release because it has a significantly negative effect on performance.  Check Ubuntu's Newsletter #82 for some datails.

---

### Post by Ub1476 on 2008-03-17
Ubuntu is slower than KISS (Keep it Simply & Stupid) distroes. Like Arch, Gentoo etc. It's mainly because Arch is optimized for i686 (Ubuntu is i386), and you have to configure your system from the beginning. Ubuntu provides an easy to install, easy to use, easy to fix etc OS, therefore it loads more stuff than some distroes. Compared to other userfriendly distroes, it's basically the same speed. Even though Ubuntu is pretty fast.

If you find Ubuntu slow, install preload:

```
sudo apt-get install preload
```

It remember commonly used apps and loads them into memory (something like that I believe).

But, Gnome is sort of a heavy DE. In Arch Linux for instance, I find KDEmod at least twice as fast than Gnome (Kubuntu feels much slower than Ubuntu though..).

---

### Post by Perpetual on 2008-03-17
In my opinion, Ubuntu runs as fast if not faster than Fedora 8, Mandriva 2007, openSuse, Debian Testing & Unstable (have tried others but these are the ones I have spent the most time with).  I would say of those mentioned, Debian may have a slightly snappier feel than Ubuntu.

Again, this is just my opinion from daily usage and I have never done any benchmarking to validate what I believe.

Landon.

---

### Post by GTvulse on 2008-03-17
On the issue of performance, it is true that you can obtain better performance if you tune up your binary images for your particular hardware, to a point. This is the small speckle of truth behind the myths dreamed by the ricer communities and quite well represented (or misrepresented depending on your particular opinion) by many early Gentoo users.

The truth is that in most cases using binaries compiled for a i486 or for a i686 in modern hardware and by modern I mean almost anything made since 2000 is irrelevant. The hardware is so fast and capable that the extra computing cycles used to process i486 compiled code has no real impact on performance. To make things clearer, las time I saw a brand new i486 in the wild was in early 1995, while the last time I saw a brand new true i686 (a Pentium Pro if my memory serves me correctly) was 1998. AMD did stick to the i686 design longer.

Performance tuning is a dark art that implies tuning lots of things in a system, but as a rule of thumb, if you want to speed up userspace, you'll start by compiling lilbc and all mathematical libraries to the specific architecture of your hardware, and even so speed increases are marginal for general use and the perceived speed up is a placebo effect. Hardware is the limiting factor on speed.

---

