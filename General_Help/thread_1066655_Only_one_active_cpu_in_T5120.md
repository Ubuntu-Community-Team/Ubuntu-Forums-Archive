---
title: "Only one active cpu in T5120"
date: 2009-02-11
forum: General Help
---

### Post by Anders Kvist on 2009-02-11
Hi

I have a T5120 which i just installed Ubuntu 7.10 on. Everything looks fine and if i do a cat /proc/cpuinfo i get:

```
cpu		: UltraSparc T2 (Niagara2)
fpu		: UltraSparc T2 integrated FPU
prom		: OBP 4.29.0.a 2008/09/15 12:01
type		: sun4v
ncpus probed	: 64
ncpus active	: 1
D$ parity tl1	: 0
I$ parity tl1	: 0
Cpu0ClkTck	: 00000000457646c0
MMU Type	: Hypervisor (sun4v)
```

Great, only one cpu active. But nomatter what i do, it will only say 1 active.

---

### Post by Anders Kvist on 2009-02-16
Apparently the 7.10 I installed had a non-SMP kernel, so the fix is just to install a SMP kernel and everything will work :)

---

### Post by dmallari on 2009-03-02
Hi,

Based on your post it seems that you were successful installing ubuntu 7.10 on a T5120. I have been trying desperately to install it and no such luck. Can you help me in the installation or email me instructions?

Really need help:(


Thanks in advance.. Dan

---

