---
title: "CPU Usage"
date: 2005-11-26
forum: Desktop Environments
---

### Post by rado_london on 2005-11-26
Hi 
Yesterday I found someting strange. I have HP Pavilion dv4145, Intel(R) Pentium(R) M processor 1.73GHz. In the terminal I entered
```
cat /proc/cpuinfo
```

This is the result
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.73GHz
stepping        : 8
cpu MHz         : 798.575
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 1576.94

```

I see that Ubuntu uses only 798.575 MHz. is there any way to do it to work at the mormal 1.7 Mhz
Thanks in advance

PS This stats are when I use my laptop with AC Adaptor plugged in

---

### Post by patrickfromspain on 2005-11-26
Why should ubuntu use 1,7Ghz while you are only running firefox por example? That's something completely normal. It's intel speedstep technology (or something similar). If you go to a pannel and click with the left button mouse on it you can choose add to the panel, and there you should see something like CPU frequency monitor. It will show you how much CPU is used... you'll how it grows when more power is needed.

---

### Post by rado_london on 2005-11-26
Thanks I done it and started OOo and it was 1.7Ghz.

---

