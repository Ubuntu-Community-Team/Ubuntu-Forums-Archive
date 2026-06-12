---
title: "Custom kernel for Latitude"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by allaboutsam on 2008-06-30
I'm trying to build a custom 2.6.25 kernel for a Latitude D400. I have the plain vanilla 2.6.25 kernel working, but would like to slim it down as much as possible.

Does anyone know where I can get detailed hardware specs for my computer?

--Does Dell provide this information anywhere?
--Or is there a third-party source?
--Or is there a software tool that will probe the hardware and print out what I have?
--Or should I open up the computer and Google the numbers printed on all the chips?

Would be much obliged for any advice from folks who have done this before.

Many thanks,
allaboutsam

---

### Post by sdennie on 2008-06-30
Is there a specific reason you want to slim it down?  If you used the Ubuntu kernel config as a basis, the vast majority of the kernel is built as modules and, apart from taking up some disk space, don't have any real impact on the performance of the kernel.  If you built using a make-kpkg and the new package/kernel is huge, you may want to build again but using the following options:

```

INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-my_version_description kernel_image kernel_headers

```

This will build a MUCH smaller kernel.  Replace CONCURRENCY_LEVEL=3 with however many threads you want to use to build at the same time and "-my_version_description" with a description of the kernel.

---

### Post by allaboutsam on 2008-07-01
vor,

Yes, I used the Ubuntu kernel config as the basis, and the kernel I built is huge. Many thanks for the suggestions. I will look into them and give them a try.

In addition to stripping out unneeded code, there seemed to be a number of cases where optimization would be possible if I knew a bit more about my hardware. Take CONFIG_HIGH_RES_TIMERS, for example. It can't be modularized, so if I don't need it, it's just wasting space. Just one of many, many examples.

I'm new at this so don't have a good sense of how much of a difference these things will make, either individually or collectively. Hence my question, "How do I find out more about my hardware?"

Thanks again,
allaboutsam

---

### Post by sdennie on 2008-07-02
I'm not sure if you are going to find the detailed information you want on the internet anywhere but, the following commands should give you some very useful information (from an Ubuntu kernel to see what modules you are using):

```

lsmod
sudo lshw
sudo dmidecode

```

You've probably noticed this but, in "make menuconfig", you can hit ? on any entry and it will give you a brief description of it and nice adivce like, "If you don't know what this means, say Yes here".

Hope that helps.

---

### Post by allaboutsam on 2008-07-02
That is very helpful. Thank you.

I had seen the "?" help, which was good as far as it went. But I'm one of those crazy people who wants to understand it all and make actual decisions, rather than just accepting the default because I can't figure it out.

---

