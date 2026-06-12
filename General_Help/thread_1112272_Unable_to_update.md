---
title: "Unable to update"
date: 2009-03-31
forum: General Help
---

### Post by jsjmac1 on 2009-03-31
I have tried to install my NVIDIA driver and I received this message:

E:  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

E:  _cache ->open ()failed, please report.

...now when I try to install anything or install updates, the same message appears.  How do I correct this?  Any help is appreciated.

---

### Post by jmszr on 2009-03-31
jsjmac1,

 In the Terminal (Applications > Accessories > Terminal) copy and paste (or type):
```
sudo dpkg --configure -a
```

When it asks for your password, type it in-you won't see it(security),and then press enter.

---

### Post by willdemon2 on 2009-04-01
Yes! This will repair the Up-date Configure. The Forums are always a quick solution for the ubuntu newbe. Thanks for the tip!

---

