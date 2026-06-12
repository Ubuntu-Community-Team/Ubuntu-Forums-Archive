---
title: "How can I get source for a driver in /usr/src?"
date: 2009-03-28
forum: General Help
---

### Post by fhydan on 2009-03-28
I'm currently using the ath9k atheros driver. My kernel is 2.6.27-11-generic and I can find the directory where the source code for ath9k would go:

```
/usr/src/linux-headers-2.6.27-11-generic/drivers/net/wireless/ath9k
```

However, the directory only contains the following:

```
fhydan@Khwarizmy:/usr/src/linux-headers-2.6.27-11-generic/drivers/net/wireless/a
th9k$ ls
Kconfig  Makefile
```

How can I get the source files for the driver version that I am currently using?

---

### Post by dcstar on 2009-03-28
> **fhydan said:**
> I'm currently using the ath9k atheros driver. My kernel is 2.6.27-11-generic and I can find the directory where the source code for ath9k would go:

```
/usr/src/linux-headers-2.6.27-11-generic/drivers/net/wireless/ath9k
```

However, the directory only contains the following:

```
fhydan@Khwarizmy:/usr/src/linux-headers-2.6.27-11-generic/drivers/net/wireless/a
th9k$ ls
Kconfig  Makefile
```

How can I get the source files for the driver version that I am currently using?

You enable the source code option in your repositories and then install the source of that particular package.

---

### Post by fhydan on 2009-03-28
Thanks for replying.
I can't figure out which package that is though. I got the driver when I installed the system so I'm not sure which package has it.  I tried searching for it but to no avail. Are there particular packages that usually have driver kernel modules? Would this be with the kernel sources??

---

