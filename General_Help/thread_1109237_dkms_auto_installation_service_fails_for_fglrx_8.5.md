---
title: "dkms auto installation service fails for fglrx 8.543"
date: 2009-03-28
forum: General Help
---

### Post by ruddha on 2009-03-28
For some reason dkms auto installation service fails for fglrx 8.543. I tried purging dkms en reinstalling fglrx drivers to no avail. Dmesg doesn't show any reference to dkms neither does syslog. Anyone has an idea how this can be solved?

```
 * Running DKMS auto installation service for kernel 2.6.27-11-generic
 *  fglrx (8.543)...                                                  [fail]
```

---

### Post by ruddha on 2009-03-28
When issuing the "prepare" command from module-assistant it became apparent that  linux-headers-2.6.27-11-generic was missing.

---

### Post by Neo_The_User on 2009-03-28
different kernel will fix the problem. -7 and -14 work fine. -9 and -11... not good.

---

