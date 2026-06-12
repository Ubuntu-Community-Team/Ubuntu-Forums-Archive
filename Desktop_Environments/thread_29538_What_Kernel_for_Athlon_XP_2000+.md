---
title: "What Kernel for Athlon XP 2000+ ?"
date: 2005-04-24
forum: Desktop Environments
---

### Post by denzilla on 2005-04-24
I was wondering what Kernel is optimized for Athlon XP 2000+ and what apt-get command for getting this Kernel is? Will it break anything if I already have the Nvidia drivers installed?

---

### Post by Xerampelinae on 2005-04-24
Uh, I think there's only one kernel option that allows you to specify your cpu type as Athlon, but that's pretty much it...

I'd say it's not worth it, unless you're already re-compiling for some reason.  I'd use the default kernel included.

---

### Post by denzilla on 2005-04-24
K, thanks for the advice :)

---

### Post by thecrimsonking on 2005-04-24
2.6.10-5-k7  is the kernel for Athlons.  I used synaptic to get it and it works great on my 2000+
If you already have Nvidia drivers installed you just have to reinstall them.  No big deal.

---

### Post by dewey on 2005-04-24
To install the k7 kernel, simply use.
```
$sudo apt-get install linux-k7
```

---

