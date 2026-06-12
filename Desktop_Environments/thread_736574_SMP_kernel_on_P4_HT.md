---
title: "SMP kernel on P4 HT?"
date: 2008-03-26
forum: Desktop Environments
---

### Post by boakes on 2008-03-26
I'm a little confused, none of the SMP kernels show up in synaptic, but I've also read that the standard 686 kernel has built in smp support, which I don't know if i believe that.  However, when I go to search for the 686 kernel, it isn't in synaptic either.  So aside from going to kernel.org and compiling my own, where can I get the 686(smp) kernel?

I have a P4 HT, yes I realize it's a single core that emulates dual cores.

---

### Post by ruibernardo on 2008-03-26
Hi boakes,

I have a P4 HT 2.8 and it uses the generic kernel.
```
$ uname -a
Linux ubuntu-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```You can check if it uses SMP by looking at "Resources" tab of System Monitor (in System > Administration). It should show 2 processors, CPU1 and CPU2.

The top command should do it too. Just run
```
$ top
```And press the '1' key to display both processors stats.

Another way to check is looking at the content of /proc/cpuinfo

$ cat /proc/cpuinfo
```
**processor       : 0**
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 5
cpu MHz         : 2800.145
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss **ht** tm pbe cid xtpr
bogomips        : 5607.48
clflush size    : 64

**processor       : 1**
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 5
cpu MHz         : 2800.145
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss **ht** tm pbe cid xtpr
bogomips        : 5600.26
clflush size    : 64
```It shows "processor 0" and "processor 1" info and in the flags "ht" is present.

This should work for you too.

---

### Post by boakes on 2008-03-26
I have the exact same processor.  When I check system monitor it only shows one processor.  So I guess both virtual cores are seen because top changes when I press 1.  Yet it doesn't show in system monitor?  Cpuinfo shows ht as well.

---

### Post by ruibernardo on 2008-03-26
What about /proc/cpuinfo?

---

### Post by TransitMan on 2008-03-26
If System Monitor is only showing one CPU, then boot into the BIOS and make sure your settings there are set for Hyper-Threading.
Then boot into Ubuntu and recheck the System Monitor.

---

### Post by boakes on 2008-03-27
Last I checked HT was enabled in the bios.  I'll look again though.


```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.426
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
bogomips        : 5590.22
clflush size    : 64
```

If I run the generic kernel, I get SMP, but I would like to run the 686 kernel, but neither the 686 kernel, nor the 686smp kernel show up in synaptic.

---

### Post by TransitMan on 2008-03-27
Simply run the generic kernel. The 686 is no longer needed to correctly run a HT processor in SMP mode. 
Besides, what does the 686 have that the Generic doesn't?

Further, according to your output, you are not seeing a HT processor in Ubuntu, therefore a look at the BIOS is in order.

---

### Post by boakes on 2008-03-27
I'm running the generic kernel now, it shows both processors.  Why is the 686 kernel not showing up in synaptic?

---

### Post by ruibernardo on 2008-03-27
The generic kernel has replaced the kernel 686 and 386 since Ubuntu 6.10 Edgy, if that's what your talking about:: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=linux+686](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=linux+686)

The generic kernel is the kernel for all i386 32 bit processors, I think. There is a amd64 generic kernel for 64 bit processors (Intel and AMD).

---

### Post by boakes on 2008-03-28
I have installed the 386 kernel for Ubuntu, but it doesn't support SMP.  I guess the generic kernel will do.

---

