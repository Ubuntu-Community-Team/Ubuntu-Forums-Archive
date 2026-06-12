---
title: "GDM Crashing"
date: 2009-08-26
forum: Desktop Environments
---

### Post by rhaces on 2009-08-26
Hi all, I've been experiencing since yesterday some GDM Crashes, I'm normally working and suddenly the Desktop Environment dies and restarts, killing all my windows and apps running in it. 

Maybe as a coincidence, Monday night i upgraded to linux-image-2.6.28-15-generic, so this can be the cause of the crashes.

Here are my specs:
```
Ubuntu 9.04 64 bit
Dell M1530 Laptop
Intel(R) Core(TM)2 Duo T6400 @ 2.00GHz
3 GB Ram
160 GB HD
```

Im uploading the :0.log when the crash happened

Thanks
Rodrigo

---

### Post by ajgreeny on 2009-08-26
Did the linux-restricted-modules of the same version get installed as well; it appears that some modules are missing from the system.

---

### Post by rhaces on 2009-08-26
> **ajgreeny said:**
> Did the linux-restricted-modules of the same version get installed as well; it appears that some modules are missing from the system.

Yes they are installed
```
$ dpkg -l |grep restricted
ii  linux-restricted-modules-2.6.28-14-generic                    2.6.28-14.19                             Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
ii  linux-restricted-modules-2.6.28-15-generic                    2.6.28-15.20                             Non-free Linux kernel modules for version 2.6.28 on x86/x86_64
ii  linux-restricted-modules-common                               2.6.28-15.20                             Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic                              2.6.28.15.20                             Restricted Linux modules for generic kernels

```

---

### Post by rhaces on 2009-08-26
another thing, I don't know if it has something to do or not, but both times that crashed, VMWare was running

Thanks

---

### Post by rhaces on 2009-09-18
Bump, got no answer, just crashed with the same error, while using VMWare Workstation

---

### Post by sam-c on 2009-09-23
[SIZE="4"]Also my gdm has been crashing for last week the x-server gets stuck or corrupted[/SIZE]
> **rhaces said:**
> Hi all, I've been experiencing since yesterday some GDM Crashes, I'm normally working and suddenly the Desktop Environment dies and restarts, killing all my windows and apps running in it. 

Maybe as a coincidence, Monday night i upgraded to linux-image-2.6.28-15-generic, so this can be the cause of the crashes.

Here are my specs:
```
Ubuntu 9.04 64 bit
Dell M1530 Laptop
Intel(R) Core(TM)2 Duo T6400 @ 2.00GHz
3 GB Ram
160 GB HD
```

Im uploading the :0.log when the crash happened

Thanks
Rodrigo

---

### Post by sam-c on 2009-09-24
Problem not solved yet, I get a Blue Screen and a message that x-server can not start and gdm is down.
It is on this computer but on a different partition.

---

