---
title: "64 or 32 bits for desktop?"
date: 2010-12-16
forum: Desktop Environments
---

### Post by fernandoch on 2010-12-16
I have a laptop with 4 GB of RAM and I am planning to install Ubuntu 10.10. 

What would you recommend? 64 or 32 bits? and why?

Thank you.

---

### Post by cipherboy_loc on 2010-12-16
Please boot the Ubuntu 10.10 LiveCD (use 32-bit) and post the output of:

```
cat /proc/cpuinfo
```

From the terminal (Applications -> Accessories -> Terminal). This will give us some info into what processor you are using/have in your system.


Cipherboy

---

### Post by fernandoch on 2010-12-16
Here is the output, although I don't understand why it is needed, my CPU is able to run 64 bits programs

```
fernando@fernando-laptop:~$ sudo cat /proc/cpuinfo
[sudo] password for fernando: 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4521.08
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
stepping	: 6
cpu MHz		: 2266.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4520.94
clflush size	: 64
power management:
```

---

### Post by 3Miro on 2010-12-16
Use 32-bit only if something in the 64 doesn't work (which is unlikely). Some printer drivers and some windows codecs may have hard time working, otherwise use 64-bit.

---

### Post by fernandoch on 2010-12-16
So why when you go to the download, it is recommended the 32 bits?

---

### Post by wojox on 2010-12-16
> **fernandoch said:**
> So why when you go to the download, it is recommended the 32 bits?

It's just easier for new people getting things setup like 3Miro said about drivers and such.

You can use 64 bit since you have the lm - long mode flag.

---

### Post by oldos2er on 2010-12-16
> **fernandoch said:**
> What would you recommend? 64 or 32 bits? and why?


For the same reason we went from 8-bit to 16-bit, 16-bit to 32-bit; to take full advantage of your hardware's capabilities.

If you choose 64-bit, Flashaid provides an easy way to install 64-bit flash. 
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by fernandoch on 2010-12-16
Why this addon? The default one does not work properly?

---

### Post by KdotJ on 2010-12-16
Some people have issues getting flash to work at first. But it is entiry possible, I got it working with no issues at all. 

I'd go with 64bit, why stay behind with the times lol

---

### Post by oldos2er on 2010-12-16
64-bit flash is not in the repositories, Flashaid makes it easy to install.

---

### Post by fernandoch on 2010-12-16
Thank you all!

---

