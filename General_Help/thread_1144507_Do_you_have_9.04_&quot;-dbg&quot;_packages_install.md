---
title: "Do you have 9.04 &quot;-dbg&quot; packages installed?"
date: 2009-04-30
forum: General Help
---

### Post by dcstar on 2009-04-30
I just removed some unwanted packages from my 9.04 system, and I noticed that I had a quantity of the debug packages installed (those ending with -dbg).

My understanding is that these are for people doing development or debugging, so I was surprised to see these on my production system installed from the RC CD. I also checked another 9.04 system I have in a VM and this also had -dbg packages.

Anyone else also have -dbg packages in their 9.04 system?

---

### Post by andrew.46 on 2009-05-01
Hi dcstar,

Oddly enough I searched my new Jaunty install:

```
sudo find / -name '*-dbg'
```

and I had none. Mind you this was from the *release* rather than the *release candidate*, perhaps this is the difference?

Andrew

---

### Post by DeMus on 2009-05-01
> **dcstar said:**
> I just removed some unwanted packages from my 9.04 system, and I noticed that I had a quantity of the debug packages installed (those ending with -dbg).

My understanding is that these are for people doing development or debugging, so I was surprised to see these on my production system installed from the RC CD. I also checked another 9.04 system I have in a VM and this also had -dbg packages.

Anyone else also have -dbg packages in their 9.04 system?

I have plenty folders ending with -dbg in /usr/share/doc but these must be folders with documentation, right?

---

