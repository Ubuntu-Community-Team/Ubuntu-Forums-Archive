---
title: "Dual Core Intel Core Duo &amp; Dapper Drake:works 1 or 2 cores?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Attila on 2006-06-11
Hi all, I'v got a laptop based on a Intel Core Duo T2400 and I've a question: on WinXP, if I launch Task Manager, I can see the activity of the 2 cores of the cpu.
On Dapper Drake if I launch System Monitor I can see the usage of the cpu but it seems that I've got a cpu single core.
Does Ubuntu recognise my cpu dual core and distribute the work on the 2 cores but it show me the 2 cores as only one, or it uses only one core and shows me effectively the load of the core that it use?

---

### Post by glotz on 2006-06-11
I'm a Linux newbie but I think that depends on what kernel you have. The default kernel only works one core. The smp kernel will work 2.

See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by RawMustard on 2006-06-11
As glotz has said, you need to install the smp kernel.  search in synaptic for kernel and install the smp one :)

---

### Post by Attila on 2006-06-11
[QUOTE=RawMustard]As glotz has said, you need to install the smp kernel.  search in synaptic for kernel and install the smp one :)[/QUOTE]
Thanks guys' I'll do it and I'll tell you if it works.

---

### Post by ronintiger on 2006-08-26
I have an Asus Centrino Duo with the same processor as you.
I´ve installed the 686 kernel (insted of the 386) and works perfectly :D  (Thanks to vanilla.gorilla \\:D/ )

When I was installing the kernel with synaptics I saw the SMP kernels also and installed them. But when I tried them out I got a Kernel panic :-s  but nevertheless the 686 kernel works ok really.
In system monitor I can see 2 CPU, and I've added 2 sysmonitors to may task bar one for each CPU :)

---

### Post by Ramses de Norre on 2006-08-26
There are no smp packages nomore in dapper, the smp support is enabled by in the 686 and k7 kernels but not in the 386 kernel.
So you need to install and use the 686 kernel in your case to use the two cores.

---

### Post by syxbit on 2006-08-26
> **Ramses de Norre said:**
> There are no smp packages nomore in dapper, the smp support is enabled by in the 686 and k7 kernels but not in the 386 kernel.
So you need to install and use the 686 kernel in your case to use the two cores.

i justs did
```
sudo aptitude install linux-686-smp
```
you can check if both cpu's are working with
```
top
```

---

### Post by Ramses de Norre on 2006-08-26
linux-686-smp is the same as linux-686..

---

