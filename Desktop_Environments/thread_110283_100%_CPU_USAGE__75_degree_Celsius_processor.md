---
title: "100% CPU USAGE | 75 degree Celsius processor"
date: 2005-12-30
forum: Desktop Environments
---

### Post by digitalkarabao on 2005-12-30
this is a repost.

my system throttles to 100% CPU usage and crashes running small applications. This does not happen in Windows XP even when i run resource-hog applications. The laptop temperature applet in gnome reports my portable is 75 degree celsius hot.

Powernowd is installed but it keeps on crashing even when I set the cpufreq selector to either conservative, ondemand or whatever cpu frequency governor.

I would like to know how to resolve this issue. Sometimes, I am only running a tagging application and the system crashes.

I need help.

---

### Post by art on 2005-12-30
When this happenes, type in the terminal 

top

and see what process is taking most CPU. That will help figuring out the problem...

---

### Post by dcstar on 2005-12-30
[QUOTE=art]When this happenes, type in the terminal 

top

and see what process is taking most CPU. That will help figuring out the problem...[/QUOTE]
Applications-System Tools-System Monitor is probably a better way to look at what is happening.

---

### Post by digitalkarabao on 2005-12-31
when i run vmware, it is vmware causing the throttling to 100%. when i use opengl billiard, the game causes the throttling. when i use easytag, it is easytag. the throttling to 100% causes the system to crash. now what? :)

i tried upgrading to the smp kernel but the issue persists.

here's my cpu info. hope this helps.

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3001.771
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5865.47

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3001.771
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5996.54

---

### Post by briancurtin on 2005-12-31
are you running the regular 686 kernel then?

the 686-SMP should work for you since you have a hyperthreaded processor. i had this same problem in SuSE and the half-assed fix i got out of my bug report wasn't very stable so i switched out and came to ubuntu and it worked better with the 686/686-SMP kernels.

---

### Post by digitalkarabao on 2005-12-31
and i believe my fans are not detected ..the /proc/acpi/fan/  is empty.

and when i run  cat /proc/acpi/thermal_zone/*/* , i receive the output below.

<setting not supported>
cooling mode:   critical
<polling disabled>
state:                   ok
temperature:             75 C
critical (S5):           85 C

what is next...arghhhhhhhh!

---

