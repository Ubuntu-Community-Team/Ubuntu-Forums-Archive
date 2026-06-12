---
title: "cpu underclock problem"
date: 2006-04-02
forum: Desktop Environments
---

### Post by whoa_551 on 2006-04-02
My 1.6GHz Intel Pentium M (Centrino) is running at only 600MHz.  Is there anything I can do to adjust this?  (And why is it clocked *so* low?) My cpuinfo:

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 6
cpu MHz         : 599.983
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1191.93
```

It's a Winbook laptop with 512MB ram...

---

### Post by dcstar on 2006-04-02
[QUOTE=whoa_551]My 1.6GHz Intel Pentium M (Centrino) is running at only 600MHz.  Is there anything I can do to adjust this?  (And why is it clocked *so* low?) My cpuinfo:

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 6
cpu MHz         : 599.983
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1191.93
```

It's a Winbook laptop with 512MB ram...[/QUOTE]
Any solution will be in your BIOS.

---

### Post by magnusbb on 2006-04-02
No, the solution is the way Ubuntu handles the frequency-scaling of your CPU (you've got a laptop, right?). Well, similar to the way Windows normally does it, Ubuntu is bundled with a daemon called "powernowd". 

Its philosophy is, that the CPU normally runs at the lowest frequency in the "scaling range" (on my computer this is 600 MHz, with a total of 1.7 GHz). When a task needs more power, for example if it demands more than 80% of the CPU, it will be raised to the highest possible level, as long as the demand for power is present.

Try to run a "sudo killall powernowd" in the terminal and see if you're confident with running without a frequency-scaler. It is certainly faster, but the laptop will also get very warm after a while, and the fan will run constantly. 

There also are other frequency-scalers for you to try; for example, you have Cpufreqd, which I use.

---

### Post by whoa_551 on 2006-04-02
[QUOTE=dcstar]Any solution will be in your BIOS.[/QUOTE]

I can't find anything about CPU clockspeed in my BIOS.


[QUOTE=magnusbb]Its philosophy is, that the CPU normally runs at the lowest frequency in the "scaling range" (on my computer this is 600 MHz, with a total of 1.7 GHz). When a task needs more power, for example if it demands more than 80% of the CPU, it will be raised to the highest possible level, as long as the demand for power is present.[/QUOTE]

So, basically my CPU's capability of running at 1.6GHz is not eliminated in Ubuntu, it just reserves it for when 1.6GHz is ***needed***...but when my computer is doing nothing, Ubuntu makes the CPU "rest" at 600MHz.  Is that what you're saying?

---

### Post by Ramses de Norre on 2006-04-02
Indeed ;)

---

### Post by whoa_551 on 2006-04-02
Very interesting...I had a hunch that it might be something like this...Thanks

---

### Post by faswad on 2006-04-06
I've done quite a bit of research on this.

Even if powernowd is killed, the kernel will still limit your cpu frequency based on what  Intel's Speedstep decides it should be, (ie 600 mhz when on battery, dynamic when plugged in). At least in my case, it was impossible to run my laptop "ondemand" or on "performance" when on batteries. There is only one way so far that I have come up with do circumvent this.

---

