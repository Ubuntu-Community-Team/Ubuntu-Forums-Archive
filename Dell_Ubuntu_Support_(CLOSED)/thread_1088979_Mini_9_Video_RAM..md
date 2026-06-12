---
title: "Mini 9 Video RAM."
date: 2009-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirebral on 2009-03-06
I have my Studio Hybrid with 8.10 and my Mini 9 with 8.04.  These two are actually comparable systems.

Studio Hybrid:
1.87GHz dual core CPU
1GB RAM
Video: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

Mini 9:
1.6 dual core CPU
1GB Ram
Video: Intel Corporation Mobile 945ME Express Integrated Graphics Controller

The differences are the Video Card and the CPU bandwidth.  This is what else I am looking at.  The vRAM on the Studio Hybrid is only slightly different then the vRAM on the Mini 9

Studio Hybrid vRAM: 
(64-bit, non-prefetchable) [size=1M]
(64-bit, prefetchable) [size=256M]

Mini 9 vRAM: 
(32-bit, non-prefetchable) [size=512K]
(32-bit, prefetchable) [size=256M]

Other then the bit size and the non-prefetchable size the vRAM is almost the same.

Now I actually have a question after these observations.  When I run emerald on my Mini 9 I have a lot of lag when I scroll through Firefox.  But when I run it on my Studio Hybrid I don,t even notice it.  Is there anything that I can do to smooth the transitions?

Here is the code to see how much vRAM your card has: 
**sudo lspci -v -s 00:02.0**

---

### Post by mpsii on 2009-03-06
Mini 9 does not have a dual core. It is single core. The dual core Atoms are the 330 series and relegated to the desktop per Intel.

---

### Post by anjilslaire on 2009-03-06
> **mpsii said:**
> Mini 9 does not have a dual core. It is single core. The dual core Atoms are the 330 series and relegated to the desktop per Intel.

Well, it certainly likes to pretend, doesn't it?

---

### Post by sirebral on 2009-03-06
> **mpsii said:**
> Mini 9 does not have a dual core. It is single core. The dual core Atoms are the 330 series and relegated to the desktop per Intel.

Tell that to my computer please.

---

### Post by techstop on 2009-03-06
> **sirebral said:**
> Tell that to my computer please.

mpsii is correct. The Mini 9 has an Atom single-core processor with HyperThreading.

EDIT: See here;

[http://ark.intel.com/cpu.aspx?groupId=36331](http://ark.intel.com/cpu.aspx?groupId=36331)

---

### Post by anjilslaire on 2009-03-06
I suspected as much, hence my comment about pretending. That, as lshw not noting anything about multiple cores, makes Hyper Threading make sense.

IMO, Hyper Threading is nothing more than an annoying marketing gimmick.

---

### Post by sirebral on 2009-03-06
#-o.

---

