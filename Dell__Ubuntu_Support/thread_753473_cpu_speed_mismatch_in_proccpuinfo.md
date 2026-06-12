---
title: "cpu speed mismatch in /proc/cpuinfo ?"
date: 2008-04-12
forum: Dell  Ubuntu Support
---

### Post by stevieP on 2008-04-12
I have somewhat of a newbie question, regarding the output of 


```
 % cat /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
stepping        : 11
cpu MHz         : 800.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4791.84
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
stepping        : 11
cpu MHz         : 800.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4786.79
clflush size    : 64 
```


The model name says the processors are 2.4 GHz. but the cpu MHz field says the processors are 800 MHz. 

That's quite a difference. Is something misconfigured? What is going on here? will my CPUs not run as fast as they were advertised? 

As a control,  the output of the same command on my work computer, gives the result it should for cpu MHz (2.4 GHz CPUs):
```
 model name      : Dual Core AMD Opteron(tm) Processor 180
stepping        : 2
cpu MHz         : 2410.989 
```

I have a dell xps M1530 laptop

here is the output of uname -a:
```
 % uname -a
Linux bowie 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux 
```

I saw on the forums somewhere that someone mentioned downloading gnome-cpufreq-applet , but this looks more like a reconfiguring tool than one to monitor the cpu speeds? Maybe I will need it in the near future, so I downloaded it. 

Thanks,

StevieP

---

### Post by shad0w_walker on 2008-04-12
It's called Frequency scaling. When the CPU is idle or using less and X% the frequency will drop to lower the power usage and heat output. It will automatically jump back to 2.4Ghz if it is needed. It can be disabled from the BIOS but you shouldn't notice any difference in performance with it so I wouldn't bother.

---

### Post by sdennie on 2008-04-13
shad0w_walker is correct.  To see the max frequency of your CPU you could use something like:

```

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq

```

The things in that directory are generally interesting if you want to understand things about CPU frequency scaling.

---

