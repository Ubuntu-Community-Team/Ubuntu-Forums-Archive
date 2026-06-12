---
title: "AMD Sempron 2800+ Temperature."
date: 2011-01-29
forum: Desktop Environments
---

### Post by tbst594 on 2011-01-29
I am both new to this forum and to Ubuntu in general.
I am running Ubuntu 10.10 (Maverick) stock kernel (2.6.35-24).

I have an older desktop with AMD Sempron 2800+ cpu.
On a couple of occasions my computer has rebooted and once or twice the BIOS stopped telling me my CPU temperature was too hot.

My CPU temp. had reached close to 100 degree (critical temp is 95 degree for my CPU based on website.).

I had never had this issue with Windows 7 so I thought it was strange (I have a dual boot at the moment). So I did a test to compare the temp on both Windows 7 and Ubuntu on my machine. The lowest my CPU temp went on Win7 was 46 degrees which was good. On Ubuntu it stayed around 60 degrees. And yes I did check to make sure both were reporting correct results and matching it against the BIOS temp reading.

I did further searching on google and figured out to solve this I needed to have CPU frequency scaling working on Ubuntu. And the stock kernel while the config file says it has built-in kernel support for powernow-k6, k7, k8 options, I get errors saying my cpufreq is not supported by my CPU. I do not have the directory /sys/devices/system/cpu/cpu0/cpufreq, so I cannot make any changes to governor settings - like making the change to ondemand to fix this.

I've also tried downloading the kernel source and building support for APM cpu idle instructions and making sure all necessary CPU frequency options are enabled.

NOTE: I also have an Intel laptop and the cpu frequency scaling works beautifully, so something specific to this AMD Sempron CPU.

So my question is, is there something that can be done to lower the temp of my CPU to below 50 degrees ? I prefer using Ubuntu to Windows 7 for everything, but I don't see any option if I CPU is always running on high, it's just bad for the CPU. There must be a way since Windows is able to bring the CPU temp down nicely.

I really appreciate any advice or help you can offer me.

Here are some outputs from my system.

% cpufreq-info 
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.


% sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +77.0°C                                    

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.42 V  (min =  +0.80 V, max =  +1.80 V)
 +3.3 Voltage:     +3.31 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.18 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.14 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    2657 RPM  (min =  800 RPM)
CHASSIS FAN Speed:   0 RPM  (min = 1200 RPM)
POWER FAN Speed:     0 RPM  (min = 1800 RPM)
CPU Temperature:   +61.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +35.0°C  (high = +45.0°C, crit = +95.0°C)  


% cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 44
model name	: AMD Sempron(tm) Processor 2800+
stepping	: 2
cpu MHz		: 1600.161
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips	: 3200.32
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc

---

