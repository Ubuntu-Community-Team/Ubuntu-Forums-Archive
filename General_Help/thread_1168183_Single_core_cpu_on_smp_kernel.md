---
title: "Single core cpu on smp kernel"
date: 2009-05-23
forum: General Help
---

### Post by Orange Kingdom on 2009-05-23
I noticed that i am using a smp kernel but my cpu is an single core cpu.
Is it better (faster) to use a kernel for a single core cpu?

---

### Post by cariboo on 2009-05-23
The kernels are generic, in other words they are compiled to work on almost anything. It automatically enable as many cores as it detects. There shouldn't be any performance hit if you only have one core.

---

