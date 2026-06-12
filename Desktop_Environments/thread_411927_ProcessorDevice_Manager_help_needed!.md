---
title: "Processor/Device Manager help needed!"
date: 2007-04-17
forum: Desktop Environments
---

### Post by Skeorx13 on 2007-04-17
I have been noticing that Ubuntu (6.10) runs a little slow on some things versus XP (which I have dualbooted). I checked out the system monitor and noticed that Ubuntu does not show my Pentium D's (830) individual cores as windoze does. It simply has one CPU listed. I checked the device manager and the system does not list the processor name. It merely lists the device as unknown. How do I update the drivers or what have you so that ubuntu correctly recognizes and utilizes my processor??? Now that I look at it, the device manager lists almost none of my system specs by name. How do I update this info?

---

### Post by Skeorx13 on 2007-04-20
Anyone? Nobody here has a pentium D or hardware not recognized??

---

### Post by AtrejuT on 2007-04-20
if you use a -generic kernel image you should be utilizing both cores, if you're using a -i386 image you are not.
what is the output of
```

uname -a
cat /proc/cpuinfo

```

---

### Post by Skeorx13 on 2007-05-13
output for those commands:

Linux 2.6.17-11-386 #2 Tue Mar 13 23:30:30 UTC 2007 i686 GNU/Linux

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 2800.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc up pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6007.62

---

### Post by Skeorx13 on 2007-05-15
I downloaded the generic kernel with SMP and Ubuntu now lists both cores.

---

