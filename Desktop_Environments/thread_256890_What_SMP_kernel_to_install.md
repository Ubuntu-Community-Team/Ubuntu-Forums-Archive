---
title: "What SMP kernel to install?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by yellowtip on 2006-09-13
Hi,

I'm running dapper on a server that's supposed to have 2 processors.

However, the current kernel only sees 1 processor (see below).

What kernel should I install to support smp for this type of processors?

root@ubuntusrv01:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Xeon(TM) CPU 3.00GHz
stepping        : 4
cpu MHz         : 3000.865
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl cid xtpr
bogomips        : 6005.97

---

### Post by italian_boy on 2006-09-13
since it is a 32bit processor (no em64t flag), the latest -686-smp kernel should be ok.

---

### Post by yellowtip on 2006-09-13
Thanks for that italian_boy.

I just installed it:
apt-get install linux-686-smp

When I reboot the server, will it automatically boot into this new kernel? I ask this because I'm working on a remote server.

If no, is there any way I can configure GRUB to load the 686-smp kernel by default?

Thanks for any help.

---

### Post by yellowtip on 2006-09-13
ok, forget my last question. I rebooted and it booted straight into the new kernel.

Only now Ubuntu sees 4 cpus (???). Does this server have quad processors, or do the 2 processors have some kind if special technology that acts like 2 processors?

root@ubuntusrv01:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Xeon(TM) CPU 3.00GHz
stepping        : 4
cpu MHz         : 3000.640
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl cid xtpr
bogomips        : 6006.49

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Xeon(TM) CPU 3.00GHz
stepping        : 4
cpu MHz         : 3000.640
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl cid xtpr
bogomips        : 6000.77

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.00GHz
stepping        : 10
cpu MHz         : 3000.640
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 5600.66

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.00GHz
stepping        : 10
cpu MHz         : 3000.640
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 5600.59

---

### Post by Ramses de Norre on 2006-09-13
Do they have hyper threading?

---

### Post by yellowtip on 2006-09-13
Ramses de Norre, I have no clue, but it would seem so.

---

### Post by nrwilk on 2006-09-13
My vote goes for two dual-core xeon chips.

Like [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16819117074") one.

nrwilk

---

### Post by italian_boy on 2006-09-14
No, they have hyper-threading, as the "ht" flag suggests ;)

---

### Post by nrwilk on 2006-09-14
> **italian_boy said:**
> No, they have hyper-threading, as the "ht" flag suggests ;)
Well, that actually doesn't tell us much.

Here's my output for```
cat /proc/cpuinfo
```
I have a 2.16Ghz dual core Intel chip, and you can see that I have an ht flag as well.

```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping        : 8
cpu MHz         : 2161.344
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 4328.47

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping        : 8
cpu MHz         : 2161.344
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 4328.47

```

---

