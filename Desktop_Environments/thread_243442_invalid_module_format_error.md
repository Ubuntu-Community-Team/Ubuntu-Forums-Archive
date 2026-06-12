---
title: "invalid module format error"
date: 2006-08-25
forum: Desktop Environments
---

### Post by dsjas297 on 2006-08-25
Hello.

I just recently compiled a kernel for my system.

Then I decided to compile the rt61 wireless driver, to use with my system. The one that comes with kernel works fin, but not perfectly.

The driver compiled, but when I tried to insert it into my kernel, this happened:

```
sudo modprobe rt61
FATAL: Error inserting rt61 (/lib/modules/2.6.15.7-ubuntu1/kernel/drivers/net/wireless/rt2600/rt61.ko): Invalid module format
```

dmesg produced this:

```
rt61: version magic '2.6.15.7-ubuntu1.custom preempt 686 gcc-4.0' should be '2.6.15.7-ubuntu1 PENTIUMIII gcc-4.0'
```

I don't know what's going on, any help is greatly appreciated.

---

### Post by dsjas297 on 2006-08-26
Well, I found this would me typically caused by compiling under a kernel different from the one you are running, but here this isn't case. I am very confused.

---

