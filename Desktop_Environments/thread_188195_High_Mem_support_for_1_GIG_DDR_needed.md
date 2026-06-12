---
title: "High_Mem support for 1 GIG DDR needed?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jrattner on 2006-06-03
Are there kernels in the repos for my Intel(R) Pentium(R) 4 CPU 3.20GHz?

Right now I'm using the i686-SMP kernel and I'm not sure if thats what I should be using.

Secondly I have 1 gig of DDR ram and I am curious if there are kernels in the repo's for my processor that have high_mem support enabled?

Anyone got any clues or comments?

---

### Post by Ramses de Norre on 2006-06-03
All kernels support more than 1Gig of ram, and if you've got a normal monocore pentium 4 without hyperthreading you'll want the i686 kernel (so no smp).

---

### Post by frying_fish on 2006-06-03
I'm running the stock 686 kernel that comes with ubuntu.

My processor is P4 2.8 Ghz Northwood with HT enabled, all that stuff works, you shouldn't need an "SMP" variant, as that is now built in to stock 686.  The SMP specific variant is a meta-package to the regular 686 I think anyway, hence not needing it

I have 2GB ram in my machine and it is detected and works fine, all 2GB is found, when using "top" can see it all there so assume its all fine.

---

### Post by jrattner on 2006-06-03
Got it, I switched to the standard i686..Thank you

---

