---
title: "unverified sources"
date: 2007-06-12
forum: Desktop Environments
---

### Post by johnbl on 2007-06-12
Read an article about smartmontools, found it - ubuntu distribution - with Synaptic package Manager without a problem. But, it is heavily cautioned with " can't be  verified " notice that assures me all sorts of evil nasties will visit me if I install the package..

Can anyone explain why a suspect package or ' unverified ' would be listed anyway and just what does all this mean.

Having noted that there are any number of threads on this package as to configuration it's obviously being applied.

Please, clear up my confusion someone, anyone.. .

Thanks

John

---

### Post by merlinus on 2007-06-12
If it is from the usual repos, then the kernel upgrade has bitten you.

```
 sudo aptitude update
```

or 

```
 sudo apt-get update
```

will fix the problem.

-merlin

---

### Post by johnbl on 2007-06-15
Thanks, you were right. Worked a treat.
Johnbl

---

