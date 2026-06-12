---
title: "Origami on a dual core Intel Atom"
date: 2010-11-15
forum: Education &amp; Science
---

### Post by roganjosh on 2010-11-15
Hi, I have an Acer Aspire Revo 3610 running Ubuntu 10.10. I've set up Folding@Home using the Origami installer, but it's set it up with 4x CPUs. I was under the impression that the dual core Atom processor only had 2x CPUs, however running this:

```
$ cat /proc/cpuinfo
```

...does return information about 4x CPUs. So is it OK to keep Folding with 4x CPUs set up (it seems slow compared to my Core2 Windows PC, but I expected that anyway), or if not, how can I change the Origami settings to 2x CPUs?

---

### Post by Blutkoete on 2010-11-16
The Intel Dual Core Atom uses hyperthreading and actually identifies itself to the OS as four cores, so everything should be fine.

---

