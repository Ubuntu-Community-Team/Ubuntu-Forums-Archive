---
title: "Does Ubuntu need special kernel options?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by Morimando on 2005-06-30
Since i switched from the standard Ubuntu kernel to 1st cko5 then 2nd 2.6.12-nitro, i got the problem that every 3rd session or such (not every time my system runs!) some problems fail to start, giving the error of a memory allocation/memory access fault.
Programs that do that are XMMS, MPlayer, OpenOffice and some (but not much) more. A restart **always** fixes it. After 1 or 2 more restarts, the problem will occur again. Also the problem won't be there if the system runs without restart.
So i guess there's something i missed to compile in, which Ubuntu needs to run properly. Any ideas?

---

### Post by skoal on 2005-06-30
Unfortunately, I don't have an answer (or suggestion) for your problem, but I do like the idea of integrating all the boot time kernel options into some sort of optional grub menu (from a patch if necessary), if that's what you were suggesting.  I don't know of such a thing at present.  Just hit 'e' then 'k' (for kernel options) and a list of all know options pops up to scroll and select from.

I think however, your particular problem may be the exception to the rule, and the -nitro patchset might have something to do with that.  I don't believe most here on Ubuntu are running that custom kernel.

\\//_

---

### Post by tomchuk on 2005-06-30
The reason none of these patches have been merged into the kernel proper is that they are experimental and break stuff - as you've experienced. If you're ready to give up stability for a marginal increase in performance, just stick with -ck.

Love, Nitro, cko and others aren't worth the hassle. Kolivas is the only performance patch maintainer who actually knows what he is doing. None of the other maintainers have ever written any kernel code, they think that the ability to shoehorn in a random assortment of patches makes them kernel developers.

---

### Post by Morimando on 2005-06-30
Hm well i never had problems with nitro kernels, i use them since 2.6.9 came out and they always ran very smoothly. But well, i'll try a normal ck patchset instead of the cko/nitro patchset to see if the problem persists..

---

