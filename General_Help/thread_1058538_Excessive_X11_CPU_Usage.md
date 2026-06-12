---
title: "Excessive X11 CPU Usage"
date: 2009-02-02
forum: General Help
---

### Post by iangoeth on 2009-02-02
Hi,

Wasn't quite sure where to put this.

I've got a refurbished HP G60-125NR laptop that I installed 32-bit xubuntu on. I updated it to have the latest software packages (including the kernel).

```
Specifications (http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01533414&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

2.00 GHz AMD Turion X2 RM-70 Dual-Core Mobile Processor
3GB RAM
NVIDIA GeForce 8200M
```

Everything is working great, and I 'activated' the NVIDIA 177 proprietary driver through the Hardware Drivers wizard without issues. Now, after getting it all configured to my liking and opening the System Monitor, I've noticed that the processor is 30-40% used while I'm not doing a single thing. I opened 'top' and it seems that X11 is resonsible for this. I do not have compositing enabled for inactive windows, or any shadowing on. Other than anti-aliasing of fonts and sub-pixel hinting, I haven't really changed much of the default desktop effects or X11 settings.

Reply if you need any more information such as my xorg.conf file.

Regards,
Ian

---

### Post by lenzoid on 2009-02-03
Hmm strange... any bad /var/log/messages or dmesg output concerning the nvidia module?

Maybe install htop and get some more info out of the process.

I would search for the chip (sudo lshw) on the net and play around with xorg.conf a bit.

---

### Post by iangoeth on 2009-02-04
/var/log/messages looks fine...

This stuff in dmesg looked odd to me though:
```
[   63.453026] CPU0 attaching NULL sched-domain.
[   63.453042] CPU1 attaching NULL sched-domain.
[   63.457279] CPU0 attaching sched-domain:
[   63.457284]  domain 0: span 0-1 level CPU
[   63.457288]   groups: 0 1
[   63.457294] CPU1 attaching sched-domain:
[   63.457296]  domain 0: span 0-1 level CPU
[   63.457298]   groups: 1 0
[   63.597077] CPU0 attaching NULL sched-domain.
[   63.597092] CPU1 attaching NULL sched-domain.
[   63.599494] CPU0 attaching sched-domain:
[   63.599499]  domain 0: span 0-1 level CPU
[   63.599502]   groups: 0 1
[   63.599508] CPU1 attaching sched-domain:
[   63.599510]  domain 0: span 0-1 level CPU
[   63.599513]   groups: 1 0
```

lshw output:
```
     *-cpu:0
          description: CPU
          product: AMD Turion Dual-Core RM-70
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 2GHz
          capacity: 2GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
```

I ended up simply disabling / removing the 177 driver and installing the 188.22 driver from NVIDIA.com. That seems to have reduced the overall CPU usage of X11 to 5-10% with or without compositing enabled. Seems like that's the lowest it's going to go, but I could have sworn that xubuntu/X11 never used that much before while idling.

---

