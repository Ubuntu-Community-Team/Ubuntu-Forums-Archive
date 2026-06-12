---
title: "Unable to Boot with Kernals 2.6.27-11 &amp; 2.6.27-9"
date: 2009-02-17
forum: General Help
---

### Post by DaveySpeedstar on 2009-02-17
This is a niggle which I've had on my computer for a while.

I run 8.10(64bit version) on a dual boot with XP-Home.  On the boot-up screen I have the choice:

Ubuntu 8.10 Kernel 2.6.27-11
Ubuntu 8.10 Kernel 2.6.27-9
Ubuntu 8.10 Kernel 2.6.24-23

as well as all the other options

However the only version of Ubuntu that will boot is the one with kernel 2.6.24-23.  when I try any of the others I get the message:

```
Starting up...
[   0.004000]   Aperture beyond 4GB. Ignoring.
```

and it just hangs there till I turn off the machine and re-boot.

It goes into XP alright, and I tried reinstalling everything a few weeks ago (even trying a different Hard Drive).

I found that loading 8.10 from a new CD produced this message, and the only way I could install  8.10 was to install 8.04, and do the upgrade, which of course loads up the new kernels.

I didn't really think about this again until last night when I downloaded the latest version of Kubuntu and tried to run it from the CD, and again on trying to boot from the CD the same message appeared.

This is in my system:

Processor: ** ******** AMD Athlon 64 X2 5000+
Motherboard: ** *** ** Gigabyte GA-MA69VM-S2
Hard Drive: ** ** * *  Western Digital WD2500AAKS Caviar SE 250GB 7200RPM SATAII/300 16MB Cache
RAM: ** *** ********** Kingston 2GB

HELP!!!

Oh - I'm still a bit new to Linux, so nice easy to understand explanations would be appreciated;)

---

### Post by DaveySpeedstar on 2009-02-18
Anyone?

---

### Post by andlinux on 2009-03-27
I have the same mobo (gigabyte ga-ma69vm-s2) and also the same problem. I bought this mobo to make a HTPC, but it's not possible.

---

### Post by andlinux on 2009-03-28
I made a small video to show what I get: [http://www.youtube.com/watch?v=zRz-BbVaacI]("http://www.youtube.com/watch?v=zRz-BbVaacI")

---

### Post by DaveySpeedstar on 2009-03-28
I've reverted back to 8.04 Hardy Heron, and everything seems to be working OK now.

@ andlinux are you trying to install the 32 or 64bit version?  I've been working with 64bit, and never thought to try 32bit.  

I might have a play around with the 9.04 when it comes out next month to see if things have been resolved

<edit>
What's an HTPC?

---

### Post by andlinux on 2009-03-29
> **DaveySpeedstar said:**
> I've reverted back to 8.04 Hardy Heron, and everything seems to be working OK now.

@ andlinux are you trying to install the 32 or 64bit version?  I've been working with 64bit, and never thought to try 32bit.  

I might have a play around with the 9.04 when it comes out next month to see if things have been resolved

<edit>
What's an HTPC?
I tried to install the 32 bit and the 64 bit version, both give the same problem.

An HTPC is a home theater pc. ( [http://en.wikipedia.org/wiki/Home_theater_PC](http://en.wikipedia.org/wiki/Home_theater_PC) )

---

### Post by andlinux on 2009-03-29
Good news, it's installing 9.04 now :)

---

