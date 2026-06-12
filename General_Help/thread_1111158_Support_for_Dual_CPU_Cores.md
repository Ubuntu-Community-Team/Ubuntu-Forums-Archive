---
title: "Support for Dual CPU Cores"
date: 2009-03-30
forum: General Help
---

### Post by MysticGold04 on 2009-03-30
Just wondering if Ubuntu enables support for more than one CPU core automatically?  Someone on one of my other forums posted this link.. I personally don't seem to have any issues, so maybe its isolated to his machine?  He's running Hardy (8.04) 

```

http://junkypc.com/enable-dual-core-processors-ubuntu/

```

---

### Post by James_Lochhead on 2009-03-30
Yea it does, as long as the application you are using has support for threads it can use both cores and obviously Ubuntu uses the cores automatically for multiple applications.

As far as I know Linux supports up to quad core. I have heard it doesn't support 8 cores yet though.

---

### Post by James_Lochhead on 2009-03-30
If you go System > Administration > System Monitor you can see both cores working if you have a dual core.

---

### Post by kpatz on 2009-03-30
Is there a way to determine which CPU(s)/core(s) a given process is using?  This information is conspicuously absent from ps, top, htop, System Monitor, etc.

I know you can set CPU affinity using schedtool or what have you, but I'm trying to see which CPU/core a process that's running is actually using at a given point in time.

Also (assuming a single threaded process, and default "all CPUs" affinity), does a process ever jump from CPU to CPU, or will it always stick to whatever CPU/core it was assigned when it was spawned?

---

### Post by 3Miro on 2009-03-30
> **MysticGold04 said:**
> Just wondering if Ubuntu enables support for more than one CPU core automatically?  Someone on one of my other forums posted this link.. I personally don't seem to have any issues, so maybe its isolated to his machine?  He's running Hardy (8.04) 

```

http://junkypc.com/enable-dual-core-processors-ubuntu/

```

I think  the article talks about boot options and not regular running.

There is also part in my /etc/inint.d/rc script that makes test and then it decided on the value CONCURRENCY.

Bu default, ubuntu is using all the cores, up to 8 (I think and if you compile our own kernel the limit is in the thousands). Most apps, however, cannot use more than one core.

Don't change the scripts in /etc unless you know what you are doing.

---

