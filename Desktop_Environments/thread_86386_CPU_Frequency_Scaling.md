---
title: "CPU Frequency Scaling"
date: 2005-11-05
forum: Desktop Environments
---

### Post by chubsmalone on 2005-11-05
I am trying to get cpu frequency scaling running on my dell inspiron 1200 laptop. 

I installed the gnome's cpu frequency scaling applet, but it always gives me an error that says:

CPU Frequency Scaling Unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

I have installed powernowd, but I get an error whenever I attempt to run it:

powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]

I am running kernel 2.6.12-9.
I don't know how to mount sysfs to /sys
lsmod shows that cpufreq and cpufreq-userspace modules are both loaded.

I tried to load some of the modules suggested in other forums and I get this error whenever I modprobe them.

#modprobe speedstep-ich
FATAL: Error inserting speedstep_ich (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-ich.ko): No such device

When I do cat /proc/cpuinfo I get:

ubuntu:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.30GHz
stepping        : 8
cpu MHz         : 1297.005
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx
bogomips        : 2555.90

I assume "stepping  :8" means that there are 8 available stepping stages, so I'm pretty sure my hardware can support frequency scaling.  Does anybody know how I can make this work?

---

### Post by shof2k on 2005-11-06
You're almost there...
1) Check for sysfs by looking for a directory called /sys.  If it's there, you've got it otherwise type "sysfs /sys sysfs defaults 0 0" into your /etc/fstab file and type "sudo mount -a" in a terminal.
2) Check for modules cpufreq and cpufreq-userspace by typing "lsmod|grep cpufreq".  If you get entries for both, your ok otherwise the modules need inserting.
3) Check your CPU is supported by powernowd by running the detection script.  Type "sudo /usr/share/powernowd/cpufreq-detect.sh".  This will give you the required module to load (check with lsmod) or say if your CPU is unsuported.  

Post the outputs from the above 3 steps and you'll get there in no time.

Note:  I managed to get powernow working under Hoary but Breezy is causing me some problems.  I'll let you know how I got on.

---

### Post by chubsmalone on 2005-11-06
Thanks for the reply.  I appreciate the help very much.  Here's the output from the three steps you asked me to do.  

/sys exists.  So that is good...

Here is my output from lsmod|grep cpufreq

root@ubuntu:~/Desktop# lsmod|grep cpufreq
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0

"#/usr/share/powernowd/cpufreq-detect.sh" returned nothing.  Is it supposed to output to the terminal or is there a log that it reports to?  

Again...thanks so much for the help here.

---

### Post by shof2k on 2005-11-08
It should return something, either the module required for powernow to work or a message explaining why it can't.  Are you running this as root / sudo?

Also it may be worth looking through dmesg to see if there are any error messages there.

Sorry I couldn't help you anymore.

---

### Post by chubsmalone on 2005-11-14
I have been doing everything as root.  I checked dmesg and the only thing that suggests anything about processors is this:

[4294679.720000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294679.720000] ACPI: Processor [CPU0] (supports 8 throttling states)

Again...this is more stuff that suggests that my processor allows throttling, but I cannot get it to work.  

Is there anybody who knows how I can get this going?

---

### Post by Nano on 2005-11-15
I'm experiencing the same problems.

---

### Post by r0ll3r on 2005-11-15
For me (Clevo notebook, Intel Celeron M, stepping 5) this is how it works:
```

modprobe speedstep-lib
modprobe p4-clockmod
modprobe freq-table
powernowd
```

You should replace p4-clockmod with the suitable cpufreq module. Modules are probably here:
```
/lib/modules/[kernel you are using]/kernel/arch/i386/kernel/cpu/cpufreq/*
```

Probably acpi-cpufreq will work in most regular cases. Try each module until one does not give you any errors.

---

### Post by mixail on 2005-12-07
I had the same problem that my CPU frequency scaling is unsupported. I followed **r0ll3r ** instructions and everything worked:p 

The problem is that when I shut down, the next time I start my laptop the CPU frequency scaling is not working.

What shall I do?:confused:

---

### Post by chubsmalone on 2005-12-07
I ended up giving up on scaling.  I found out that the celeron processors can modulate frequency, but not voltage.  After some research, it seems that the frequency throttling provides very little advantage in terms of power saving.  Therefore, I just gave up on the whole endeavor.  
Good luck.

---

