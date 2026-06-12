---
title: "configure can't find bison or byacc"
date: 2004-12-09
forum: Desktop Environments
---

### Post by jamaas on 2004-12-09
I'm attempting to compile the newest version of ximian evolution (2.0.3) but can't get past configure which gives me the following

checking for bison... no
checking for byacc... byacc
configure: error: You need bison to build Evolution


I've checked and reinstalled both bison and byacc using synaptic, so both are present but still no luck.  Any idea what I've done wrong or how to correct it?

Thanks a bunch

Jim

---

### Post by willis on 2004-12-10
run "sudo apt-get install bison byacc", just to be sure... but also a more recent evolution is in hoary anyway.

---

