---
title: "Check my clock speed??"
date: 2009-03-04
forum: General Help
---

### Post by WatchingThePain on 2009-03-04
Yowser,

I've went into the bios and overclocked the processor a little.
Now how do I check my overclocked speed from the shell?.
It worked fine and of course the new speed shows in the bios.
cat /proc/cpuinfo has lots of info but not what I need.
Any idea's folks?

---

### Post by Nepherte on 2009-03-04
```
cat /proc/cpuinfo
```
should give you the frequency you are using.

This is my output:
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 43
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 1
**cpu MHz		: 1000.000**
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
bogomips	: 2011.04
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

---

### Post by anubhavrocks on 2009-03-04
Also you can try:
```
 hwinfo --cpu
```

---

### Post by stchman on 2009-03-04
> **WatchingThePain said:**
> Yowser,

I've went into the bios and overclocked the processor a little.
Now how do I check my overclocked speed from the shell?.
It worked fine and of course the new speed shows in the bios.
cat /proc/cpuinfo has lots of info but not what I need.
Any idea's folks?

I too would like to know this as well.  I have a Core 2 Quad Q6600 OCd to 3.0GHz from 2.4GHz.  Ubuntu still reports 2.4GHz while Windows Vista reports 3.0GHz.

It would appear that Ubuntu reads the ID string of the processor.

Thanks.

---

### Post by DeMus on 2009-03-04
> **stchman said:**
> I too would like to know this as well.  I have a Core 2 Quad Q6600 OCd to 3.0GHz from 2.4GHz.  Ubuntu still reports 2.4GHz while Windows Vista reports 3.0GHz.

It would appear that Ubuntu reads the ID string of the processor.

Thanks.

I OC'd my CPU the same as you and when I perform:

```
cat /proc/cpuinfo
```

I do get the 3000.055MHz the processor is using.
I did however switch the Intel Speedstep in the Bios. Now my CPU is always running at full speed. Maybe this has something to do with the info you get and which is different from the data I get.

---

### Post by emarkay on 2009-03-04
FWIW here's my "stock" data:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) D CPU 2.80GHz
stepping	: 7
cpu MHz		: 2792.938
cache size	: 1024 KB
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
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 5585.87
clflush size	: 64
power management:

---

### Post by fyo on 2009-03-04
It's not from the shell, but you can add a frequency monitor to you desktop panel.

Just right-click on the panel, select "Add to panel" and find "CPU Frequency Scaling Monitor and add it.

This will show you the current frequency of (any of your) CPU core(s). If your processor changes frequency while running, it updates (thus the "scaling" part of the name). Typically, modern processors scale the CPU frequency, throttling down if its resources aren't needed.

---

### Post by anubhavrocks on 2009-03-04
From the shell
 ```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```

---

