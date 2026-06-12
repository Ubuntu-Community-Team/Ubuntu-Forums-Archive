---
title: "Anyone Else Having Package Issues With KDE4?"
date: 2008-01-08
forum: Desktop Environments
---

### Post by jlacroix on 2008-01-08
KDE 4.0 drops Friday as far as I know. I've been trying out the KDE4 betas and release candidates for some time now and things have been going horribly.

I've tried KDE 4.0 RC2 on (at least) three machines. On each one, one of them being 64-bit and the others being 32-bit, installing KDE4 will always result in a broken package database. I have to force all the packages to install each time, which results in some packages not being completely installed or some features altogether missing.

What's worse, is not all packages are installable. Some of them depend on dependencies that don't exist.

My question is this: Will the final 4.0 have these same problems? If the way things are now are any indication, we're in for a world of hurt and broken packages. Hopefully since the packages we have now are not the final ones the problems will be fixed before they are installable.

In the meantime, isn't there a way to do an apt-get install on the packages you want, but do it in simulation mode and not make any changes?

---

### Post by exactopposite on 2008-01-08
> **jlacroix said:**
> KDE 4.0 drops Friday as far as I know. I've been trying out the KDE4 betas and release candidates for some time now and things have been going horribly.

I've tried KDE 4.0 RC2 on (at least) three machines. On each one, one of them being 64-bit and the others being 32-bit, installing KDE4 will always result in a broken package database. I have to force all the packages to install each time, which results in some packages not being completely installed or some features altogether missing.

What's worse, is not all packages are installable. Some of them depend on dependencies that don't exist.

My question is this: Will the final 4.0 have these same problems? If the way things are now are any indication, we're in for a world of hurt and broken packages. Hopefully since the packages we have now are not the final ones the problems will be fixed before they are installable.

In the meantime, isn't there a way to do an apt-get install on the packages you want, but do it in simulation mode and not make any changes?

the problem is with the naming of the packages. there are 3.96 packages in the gutysy backports repo right now, but the pacakges on the repo listed at the kubuntu site are now 3.98. the 2 sets of packages aren't named the same way. i had this same problem a couple of days ago before i noticed the difference. almost all of the later packages end with -kde4. since they aren't named the same way they conflict with eachother.

---

### Post by bench on 2008-01-08
To do a simulation do

apt-get install -s <package1> <package2> etc

---

### Post by jlacroix on 2008-01-08
Thanks guys, I hope these problems are ironed out by the time KDE 4.0 drops.

---

