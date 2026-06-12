---
title: "Kernel screw up"
date: 2009-04-11
forum: General Help
---

### Post by alzorz on 2009-04-11
I screwed up one of my kernels(have 2) the one i screwed up where 2.6.27-11-generic so i now went back to 2.6.27-7-generic which is working. Now im wondering have to remove the 11-generic kernel and get a new one so i still have a kernel to chrash with a saftey backup kernel??

Alzorz

---

### Post by Berserker v7 on 2009-04-11
Reinstall the 2.6.27-11 kernel with the command ```
sudo apt-get install --reinstall linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
```

---

### Post by alzorz on 2009-04-11
thanks alot worked perfectly

---

