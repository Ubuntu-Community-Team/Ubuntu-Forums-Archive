---
title: "Why is ubuntu-desktop dependent on OpenOffice"
date: 2006-06-09
forum: Desktop Environments
---

### Post by acolic on 2006-06-09
Hi,

I tried to remove OpenOffice from my system last night and synaptic told me that if I did then ubuntu-desktop would be removed as well.

My question is why is Ubuntu-Desktop (Dapper) dependent on OpenOffice.

OpenOffice runs too slow on my old machine so I installed Abiword. I was hoping to reclaim the space.

Any suggestions?

Thanks

Alex

---

### Post by an.echte.trilingue on 2006-06-09
ubuntu-desktop is just a meta-package that depends on all of the standard ubuntu packages to make sure that they get installed properly.  You can remove it safely and everything else should be just fine.

---

### Post by lawngn0mex on 2006-06-09
You try removing them, and then putting ubuntu-desktop back? It might only be a one way dependency.

---

### Post by unf on 2006-06-09
I dont really no why there is no "(meta)" after the ubuntu-desktop like this > ubuntu-desktop(meta)

---

### Post by acolic on 2006-06-09
Thanks, I will try that.

Alex

---

