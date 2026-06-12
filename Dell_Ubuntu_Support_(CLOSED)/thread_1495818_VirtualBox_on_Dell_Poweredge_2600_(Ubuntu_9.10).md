---
title: "VirtualBox on Dell Poweredge 2600 (Ubuntu 9.10)"
date: 2010-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by theSuperman on 2010-05-28
I have been using VirtualBox 3.2 on an old Dell Poweredge 2600. It has two dual-core Xeon processors (2800mhz), and it runs pretty snappy. I am able to run more than one VM at a time. But the issue I am running into is when I want to run just one VM. I am trying to do Android app development on a WinXP VM, however it only uses maybe 20% cpu usage in total, while the WinXP VM sees it using 100%cpu. 

Through using 'top' on the host OS, it looks like each processor is being utilized a little. I tried increasing (well actually decreasing) the niceness to -20, but I still dont see any extra processing power going to my VirtualBox VM.

Any ideas?

---

### Post by fro1269 on 2010-05-28
the way to get the best performance is to have a processor that supports virtualization (which the 2600 does not) and use a virtual environment that supports hyper-v like vmware

---

### Post by theSuperman on 2010-05-29
> **fro1269 said:**
> the way to get the best performance is to have a processor that supports virtualization (which the 2600 does not) and use a virtual environment that supports hyper-v like vmware

Well I think that Virtualbox supports multiple cores.  I figured that the processors were too old to support virtualization.  Im not too familiar with those technologies, but I figured that the OS would schedule the process across all cores, using as much processing power as needed...

---

