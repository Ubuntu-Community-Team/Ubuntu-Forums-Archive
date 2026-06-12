---
title: "kio_http sucking CPUs"
date: 2008-12-29
forum: Desktop Environments
---

### Post by John Jason Jordan on 2008-12-29
I have Intrepid x86_64 on my laptop using Gnome desktop, however I also have a number of KDE apps installed. One of them is ktorrect, which is currently running with a couple of torrents.

I am experiencing very slow, jerky system performance in spite of the fact that I have a fast Intel dual core CPU. When I look in top I see that there are three instances of kio_http running, taking roughly 60% CPU power each, leaving very little processing power for everything else. For example as I type this the system hangs for five-ten seconds after every couple of sentences.

System resources are reported as:

Release 8.10 (Intrepid)
Kernel Linux 2.6.27-9-generic
Gnome 2.24.1
Memory 3.8 GiB
Processor 0: Intel(R) Core(TM) Duo CPU T7300 @2.00GHz
Processor 1: Intel(R) Core(TM) Duo CPU T7300 @2.00GHz
Available disk space: 60.7 GiB

What does the kio_http process do? Why are there three of them running? How can I get the running apps to play nice?

---

### Post by ingo on 2009-04-28
Same here on ArchLinux and KDE4. This got me my system back: ```
killall kio_http
```But what does it do? I don't know...

Anyway, for the sake of completeness:```
toad@deskarch 990\7 ~ > kde4-config --version
Qt: 4.5.0
KDE: 4.2.2 (KDE 4.2.2)
kde4-config: 1.0
```

---

