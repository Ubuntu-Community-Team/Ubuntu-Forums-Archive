---
title: "Synaptic package manager problems"
date: 2009-03-04
forum: General Help
---

### Post by dpreed77 on 2009-03-04
Hi, 
i am using Ubuntu 8.10. I just tried to open the synaptic package manager and i get this error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am a beginner with Linux and i do not know what to do, can someone explain to me how to fix this?
Thanks,
Dennis

---

### Post by taurus on 2009-03-04
Close down synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dpreed77 on 2009-03-05
thank you!

---

### Post by mb_webguy on 2009-03-05
I know I've said it before, but this really needs to be in a sticky post or elsewhere newbies can easily find it.  I see posts identical to this one every couple of days, it seems.

---

