---
title: "8GB RAM in system, only finds 3.2GB"
date: 2009-02-01
forum: Desktop Environments
---

### Post by wiltors on 2009-02-01
Hello, I'm new to the forums as this is my first post. I'm a long time computer user and I've been using Ubuntu Linux for about 4 months, but I have a few year's experience with the Linux system, BASH and Gnome.

Just today I built myself a new system, which uses the EP45-UD3P motherboard by Gigabyte. It works great, (and looks great, acrylic case) so far, except for one problem.

I bought, and properly installed 8 GB of DDR2 RAM, yet when I check my system monitor, it says there is only 3.2 GB of memory and 2.9 GB of swap. Is this a problem with Ubuntu? Does anybody who has this board have this problem too? Halp please.

Thanks,
Wiltors

(pic attached, my new system :D)

[CENTER][IMG]http://photos-a.ak.fbcdn.net/photos-ak-snc1/v2056/205/12/1226052227/n1226052227_30322632_1428.jpg[/IMG][/CENTER]

---

### Post by taurus on 2009-02-01
Sounds like you are installing the x86 (32bit) version.  If you want to use all the RAM on your machine, you can either install the server version (x86) or the x86_64 (64bit) version.

---

### Post by wiltors on 2009-02-01
Okay, I'll try that. Thanks.

---

### Post by mhh91 on 2009-02-01
the 32-bit systems can't detect more than 4 GB's of memory,that's from what i've heard


try installing the 64-bit version :)

---

### Post by Brebs on 2009-02-01
You just need a kernel that's compiled with [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) - see [thread](http://forums.gentoo.org/viewtopic-p-4103165.html#4103165).

$ free -m
             total       used       free     shared    buffers     cached
Mem:          6083        485       5598          0         42        240

That's 6 gigs.

$ grep PAE /usr/src/linux/.config
CONFIG_X86_PAE=y

---

### Post by Mindless Automata on 2009-02-01
I think that nowadays it's generally a good idea to go 64-bit when you can.  All (?) new processors that have been coming out for awhile now are 64-bit and you'd be missing the benefit 64 bit gets on x86.  Most of the kinks and compabitility issues have been ironed out since the introduction of 64-bit processors (oh, what a pain in the *** things were back then!) and the upsides at this point outweigh, for the most part, the few (if any) downsides left.

Now if more programs were just compiled for 64-bit...

---

### Post by IanW on 2009-02-01
> **Mindless Automata said:**
>  All (?) new processors that have been coming out for awhile now are 64-bit

Netbook CPUs (Intel Atom/Via C7-M) are still 32-bit.

Wiltors - The others are correct. Ubuntu64 is the way to get all 8GB to show.

---

### Post by binbash on 2009-02-01
there is a tutorial at tutorial section about this.Read it

---

### Post by boof1988 on 2009-02-01
> **binbash said:**
> there is a tutorial at tutorial section about this.Read it

Can you post a link... please?

---

### Post by steveneddy on 2009-02-01
Just run the 64 bit version.

---

