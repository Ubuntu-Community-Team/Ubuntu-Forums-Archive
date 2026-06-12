---
title: "How to debug completely freeze"
date: 2015-12-11
forum: Desktop Environments
---

### Post by sthor69 on 2015-12-11
I experience some completely freeze of my Ubuntu Desktop (14.04 64bit) from time to time, typically related to browsing activities. During the freeze the only way to restore operations is a complete shut down. Ctrl + F2 or similar does not work.
Looking into the log files I cannot find any hint on where the problem can arise.
I looked at the kern.log and the last log before I reset the machine is always

perf samples too long (2517 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

Where can I look at for more information on the causes of the freeze?

---

### Post by ian-weisser on 2015-12-12
Is there a particular sequence of websites or browser activity you can do that will reliably reproduce the freeze?
Do you have the linux-tools-common package installed?

---

