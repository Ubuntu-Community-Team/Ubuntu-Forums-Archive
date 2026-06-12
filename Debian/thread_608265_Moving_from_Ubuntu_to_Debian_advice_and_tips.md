---
title: "Moving from Ubuntu to Debian: advice and tips"
date: 2007-11-09
forum: Debian
---

### Post by samjh on 2007-11-09
After a solid year of using Ubuntu, I'm seriously considering a move to Debian.  The reasons are mainly Debian's stability, alleged increase in speed, and much-touted customisability, not to mention the educational experience of using a more foundational distro.

I'd like some advice from those who have been-there-done-that:

What is the difference between Ubuntu and Debian with regard to installing native NVidia drivers (I've read the Debian wiki, but it's a bit over my head)?

How does Debian treat native multmedia codecs differently from Ubuntu?

Does Debian Etch/Lenny have issues with JMicron RAID controllers (I had massive problems with this and Ubuntu Edgy)?

How stable is Debian Lenny compared with Ubuntu stable releases?  What about compared with Debian Etch?  Is it more difficult to use?

What are other pitfalls to watch out for?

---

### Post by kerry_s on 2007-11-09
> **samjh said:**
> After a solid year of using Ubuntu, I'm seriously considering a move to Debian.  The reasons are mainly Debian's stability, alleged increase in speed, and much-touted customisability, not to mention the educational experience of using a more foundational distro.

I'd like some advice from those who have been-there-done-that:

What is the difference between Ubuntu and Debian with regard to installing native NVidia drivers (I've read the Debian wiki, but it's a bit over my head)?

How does Debian treat native multmedia codecs differently from Ubuntu?

Does Debian Etch/Lenny have issues with JMicron RAID controllers (I had massive problems with this and Ubuntu Edgy)?

How stable is Debian Lenny compared with Ubuntu stable releases?  What about compared with Debian Etch?  Is it more difficult to use?

What are other pitfalls to watch out for?

debian nvidia= not as easy, i just use the stock nv
codecs= dead simple, you just add the repo and install what ever you want.
raid= never used it, sorry
stabilty= very stable, you can run a etch/lenny system if you don't trust yourself. i'm running a etch/lenny/sid install, you just got read and understand updates.

pitfalls= i can't really think of any, moving to debian was the best move i made. also i don't do regular installs, i start with a base install and build up from there, installing only what i want.
wait just thought of 1, watch out for the 2.6.22 kernels, they don't work for everyone. i use the 2.6.18.5 which works perfectly for me.

my sources.list
```

deb http://www.debian-multimedia.org sid main
deb http://ftp.debian.org/debian/ lenny main non-free contrib 
deb http://ftp.debian.org/debian/ sid main non-free contrib 
deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 


```

---

### Post by tturrisi on 2007-11-11
see one of my sites:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)

---

### Post by juxtaposed on 2007-11-12
I moved from Ubuntu to Debian awhile ago (after trying feisty) and I think it's great. The nearest I've ever seen to the perfect OS.

Your results may vary though.

---

### Post by samjh on 2007-11-12
I'm having problems with the Etch installer.  I've posted on the Debian help forums for advice.  If anyone here has advice to give, I'd be glad to take them.

See here: [http://forums.debian.net/viewtopic.php?t=21248](http://forums.debian.net/viewtopic.php?t=21248)

---

### Post by ispmarin on 2007-11-13
Debian is faster. And I´ve never had any problems using the binary installer from NVIDIA.

---

### Post by jinx099 on 2007-11-13
> **ispmarin said:**
> Debian is faster. And I´ve never had any problems using the binary installer from NVIDIA.

Agreed, just make sure you have your kernel headers installed.

---

### Post by cprofitt on 2007-11-14
I used buntu for about 30 days and moved to Debian. I also tried Gentoo... and personally Gentoo was much more of a learning experience... but I didn't think it was worth actually running.

Debian is the distro for me; for now.

---

### Post by samjh on 2007-11-15
With Gentoo, you tend to learn Gentoo's customised Linux, rather than Linux in general.

I'm still pondering how to get around the freezing problem after the installer retrieves packages.  I just tried a Debian install in VirtualBox and it ran perfectly.  Perhaps the problem is with my hardware?  Hard to say.

I'm going to download the xfce iso and try installing Debian again as soon as I have time.

---

### Post by tdrusk on 2007-11-17
> **samjh said:**
> With Gentoo, you tend to learn Gentoo's customised Linux, rather than Linux in general.

I'm still pondering how to get around the freezing problem after the installer retrieves packages.  I just tried a Debian install in VirtualBox and it ran perfectly.  Perhaps the problem is with my hardware?  Hard to say.

I'm going to download the xfce iso and try installing Debian again as soon as I have time.

When it says retrieving packages, it is retrieving them from the cd. Reburn the cd at a slower speed.:guitar:

---

### Post by ZipoTe on 2007-11-17
My advice: prepare yourself :lolflag:

No, seriously, don't worry. [Debian Forums]("http://forums.debian.net") are great and have lots of howto with many information and the users are very experienced (i'm not saying here are not O:)) You will learn a lot about linux, believe me :)

---

