---
title: "AMD powernowd-k8 : overclock ok in memtest86+ and boot : won't OC in Ubuntu"
date: 2009-03-07
forum: General Help
---

### Post by hanasaki on 2009-03-07
Below are the specs and output.  Short version:
AMD Dual Core 4850e stepping 02 overclocked to 2875.228 MHz From 2.5GHz
* shows faster speed when boot into memtest86+
* shows faster speed in boot diagnostics
* powernowd only shows max speed of 2.5GHz
?? How do I get this to run faster in Ubuntu?

CPU Frequency Scaling Monitor only shows only 1.0, 1.8, 2.0, 2.2, 2.4, 2.5

Turning off the powernowd makes the cpu (both cores) run at 2.5 not the 2.8

========
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2500000 2400000 2200000 2000000 1800000 1000000
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
2500000
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative userspace powersave ondemand performance 

echo "2800000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed => sets to 2.5GHz

Mar  7 08:23:25 local-desktop powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens 
Mar  7 08:23:25 local-desktop powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit 
Mar  7 08:23:25 local-desktop powernowd:   cpu0: 1000Mhz - 2500Mhz (31 steps) 
Mar  7 08:23:25 local-desktop powernowd:   cpu1: 1000Mhz - 2500Mhz (31 steps)
[    3.646535] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e processors (2 cpu cores) (version 2.20.00)
[    0.269726] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    3.646587] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[    3.646589] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[    3.646591] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[    3.646592] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[    3.646593] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[    3.646595] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16

[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2875.228 MHz processor.

[    0.007921] ACPI: Checking initramfs for custom DSDT
[    0.229584] Setting APIC routing to flat
[    0.229934] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.269726] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    0.272001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5735.58 BogoMIPS
 (lpj=11471174)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.004000] Switch to broadcast mode on CPU1
[    0.356163] CPU1: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    0.356172] Brought up 2 CPUs
[    0.356174] Total of 2 processors activated (11486.04 BogoMIPS).
[    0.356212] CPU0 attaching sched-domain:
[    0.356214]  domain 0: span 0-1 level CPU
[    0.356216]   groups: 0 1
[    0.356220] CPU1 attaching sched-domain:
[    0.356221]  domain 0: span 0-1 level CPU
[    0.356222]   groups: 1 0

---

### Post by dcstar on 2009-03-07
> **hanasaki said:**
> Below are the specs and output.  Short version:
AMD Dual Core 4850e stepping 02 overclocked to 2875.228 MHz From 2.5GHz
* shows faster speed when boot into memtest86+
* shows faster speed in boot diagnostics
* powernowd only shows max speed of 2.5GHz
?? How do I get this to run faster in Ubuntu?

CPU Frequency Scaling Monitor only shows only 1.0, 1.8, 2.0, 2.2, 2.4, 2.5

Turning off the powernowd makes the cpu (both cores) run at 2.5 not the 2.8

========
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2500000 2400000 2200000 2000000 1800000 1000000
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
2500000
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative userspace powersave ondemand performance 

echo "2800000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed => sets to 2.5GHz

Mar  7 08:23:25 local-desktop powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens 
Mar  7 08:23:25 local-desktop powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit 
Mar  7 08:23:25 local-desktop powernowd:   cpu0: 1000Mhz - 2500Mhz (31 steps) 
Mar  7 08:23:25 local-desktop powernowd:   cpu1: 1000Mhz - 2500Mhz (31 steps)
[    3.646535] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e processors (2 cpu cores) (version 2.20.00)
[    0.269726] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    3.646587] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[    3.646589] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[    3.646591] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[    3.646592] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[    3.646593] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[    3.646595] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16

[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
**[    0.000000] Detected 2875.228 MHz processor.**
......

It already does.

---

### Post by hanasaki on 2009-03-07
Yes. It detects the faster speed; the issue is that there is no way to get it to run at the faster speed.  The gnome applet only shows upto 2.5 not 2.8 and:

[LIST]
[*]Mar  7 08:23:25 local-desktop powernowd:   cpu0: 1000Mhz - 2500Mhz (31 steps)
[*] Mar  7 08:23:25 local-desktop powernowd:   cpu1: 1000Mhz - 2500Mhz (31 steps)
[/LIST]
notice the upper limit is 2.5 not 2.8+ and:

[LIST]
[*]cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
[*]2500000 2400000 2200000 2000000 1800000 1000000
[/LIST]

---

### Post by dcstar on 2009-03-07
> **hanasaki said:**
> Yes. It detects the faster speed; the issue is that there is no way to get it to run at the faster speed.  The gnome applet only shows upto 2.5 not 2.8 and:

[LIST]
[*]Mar  7 08:23:25 local-desktop powernowd:   cpu0: 1000Mhz - 2500Mhz (31 steps)
[*] Mar  7 08:23:25 local-desktop powernowd:   cpu1: 1000Mhz - 2500Mhz (31 steps)
[/LIST]
notice the upper limit is 2.5 not 2.8+ and:

[LIST]
[*]cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
[*]2500000 2400000 2200000 2000000 1800000 1000000
[/LIST]

Those numbers are built into the CPU and are not affected by any clock changes.

---

### Post by hanasaki on 2009-03-07
so how can I both control and see the actual speed?

---

### Post by pianoman8 on 2009-03-08
Author of powernowd here. 

First, if you're using anything newer then gutsy, then "/etc/init.d/powernowd" just loads the 'ondemand' cpufreq governor (which does the same thing) and not the real powernowd, but I doubt either will do what you want. 

You've overclocked your processor, good for you. 

But hardcoded in your BIOS is an ACPI table (regardless of your overclock) that says "these are the values you can run at", and those values are what's listed in scaling_available_frequencies.  Powernowd (and anything else that uses cpufreq, like the gnome cpu frequency applet), reads that scaling_available_frequencies file to find out what values are valid, and can only use them.  Unless you also hack the acpi table in the bios to show your "overclocked" speed, nothing involving cpufreq will allow you to use the new speed. 

This isn't a powernowd problem, or even a cpufreq problem (it's doing exactly what it's supposed to do).  Bottom line, if you're going to overclock your CPU, you can't use cpu frequency scaling, or else it will reset your overclock back into known parameters. Note you might be able to get away with a FSB overclock, if powernow/eist only change frequency and voltage, but the numbers shown in Linux might still be wrong..you'd have to run an actual speed test to verify, try 'x86info --mhz' 

You'd have to keep all cpufreq programs from running, so that the kernel will keep using the default speed the bios set the processor to, and it will never spin down to save power.  There's a small chance it's just the numbers in linux are wrong, and even though it says 2.5Ghz, it really means 2.8ghz.. it depends on how the bios is implemented.  but I honestly doubt it. 

Good luck.
-pm

---

### Post by hanasaki on 2009-03-08
Thank you for the reply... fro the content, I think you are saying that there may be no real way to tell nor control it at overclocked speeds for sure. As you can see from the below two runs of x86info, it doesn't really look like those results will be that much use... both were run on a relatively idle machine (5 - 2739734GHz) results ... Wow! if only it would run at the higher number ... 

x86info --mhz
CPU #1 - two runs below
5.55GHz processor (estimate)
2739734.10GHz processor (estimate)

---

### Post by dcstar on 2009-03-09
> **pianoman8 said:**
> Author of powernowd here. 
.......
This isn't a powernowd problem, or even a cpufreq problem (it's doing exactly what it's supposed to do).  Bottom line, if you're going to overclock your CPU, you can't use cpu frequency scaling, or else it will reset your overclock back into known parameters. Note you might be able to get away with a FSB overclock, if powernow/eist only change frequency and voltage, but the numbers shown in Linux might still be wrong..you'd have to run an actual speed test to verify, try 'x86info --mhz' 

You'd have to keep all cpufreq programs from running, so that the kernel will keep using the default speed the bios set the processor to, and it will never spin down to save power.  There's a small chance it's just the numbers in linux are wrong, and even though it says 2.5Ghz, it really means 2.8ghz.. it depends on how the bios is implemented.  but I honestly doubt it. 


It looks like has has done the FSB overclock, which is why his system boot reports the actual (higher) CPU clock rate.

AFAIK the preset stepping speeds will always show the "unclocked" rates, no matter that the CPU is now actually running at the higher clock rate - so the system **is** running at the overclocked rate, it is just the utility cannot reflect that in the numbers it displays.

---

### Post by hanasaki on 2009-03-15
An interesting not to add to this...  I turned off (in BIOS setup) the features that enable CPU scaling.  The system now runs at full overclocked speed of 2.8+GHz constantly and this is reflected in /proc/cpuinfo as well as the gnome cpu applet.  Of course the software for controlling the cpu reports it cannot due so since the BIOS features are turned off.

---

### Post by kyselejsyrecek on 2010-04-18
Well, I know that this thread is about a year old, but I am affected by the issue in Ubuntu 9.10.

I overclocked my PC, setting "FSB" from 200MHz to 222MHz, that is 2GHz for my AMD Athlon 64 2800+ with multiplier 9x.

I don't agree with pianoman8.
If the 100% freq is really 1.8GHz for my CPU (that doesn't agree with BIOS settings - 222MHz, 9x multiplier), then powernowd or whatever changes the frequency shows the right value.
But this means, that the frequency-changing sw changed FSB frequency back to 200MHz (I don't know, if this is really possible, maybe another proof, that the frequency is badly computed). This is surely not right behavior and should use FPS values given by BIOS for changing frequencies.
Also if these frequency values shown are bad, and the CPU really works on 2GHz, the program should return 2GHz as well, multiplying the real FSB frequency by CPU multiplier, not to consider FSB to be normal 200MHz!

If I disable the PowerNow! function in BIOS settings, the Gnome panel applet fires a warning message that CPU frequency scaling is not supported, and (as supposed) shows 2GHz as the actual CPU frequency.
Also Hardinfo shows 2GHz with PowerNow! disabled and the actual frequency (1GHz or 1.8GHz) with PowerNow! enabled. So getting correct frequency values IS possible.

I am convinced, that the system observes enough information and is able to compute correct frequency values for these overclocked cases. Windows does it brilliantly. So what the heck is wrong in the linux module?!

---

