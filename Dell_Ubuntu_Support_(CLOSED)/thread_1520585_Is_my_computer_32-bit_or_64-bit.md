---
title: "Is my computer 32-bit or 64-bit?"
date: 2010-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d6d24r94 on 2010-06-29
Hello,

I have Ubuntu 9.10 running from a USB stick only - there is NOTHING on the hard drive except for an NTFS file system. My goal is to get Windows XP Home Edition back on my computer, but I lost the restore discs and I don't know what type it is.

My processor is an Intel Pentium 4, and I don't know the speed, but is there a way to get Ubuntu to tell me if the computer is 32 or 64-bit?

Thanks.

---

### Post by mhgsys on 2010-06-29
run 
```
grep lm /proc/cpuinfo
```

if it's capable 64 bit it will return [COLOR="Red"]lm[/COLOR]

f.e 
64 bit returns lm in it's flags:

```
fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx [COLOR="Red"]lm[/COLOR] constant_tsc up arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_[COLOR="Red"]lm[/COLOR]

```

32 bit will not return anything with grep lm.

the flags however can be found with 
```
grep flags /proc/cpuinfo
```

f.e  ```
fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up

```

Also use 
```
cat /proc/cpuinfo
```
to get to know more about your cpu

btw: A 64 bit live cd will just not run on a 32 bit cpu.

---

### Post by Sonsum on 2010-06-29
Haha. Found a 2003 thread here: [http://www.velocityreviews.com/forums/t308180-pentium-processor-is-it-32-or-64-bit.html]("http://www.velocityreviews.com/forums/t308180-pentium-processor-is-it-32-or-64-bit.html")

> P4's are 32 bit

It's very funny to see people amazed that they have 64 bit processors in laptops. :lolflag:

---

### Post by julianb on 2010-06-30
A google search says that Pentium4 64bit CPUs have existed since 2005.

In other words, [some P4 processors are compatible with a 64bit OS and others are not]("http://en.wikipedia.org/wiki/Pentium_4").

---

### Post by Sonsum on 2010-07-02
> **julianb said:**
> A google search says that Pentium4 64bit CPUs have existed since 2005.

In other words, [some P4 processors are compatible with a 64bit OS and others are not]("http://en.wikipedia.org/wiki/Pentium_4").

Okay then, I'd advise running the commands given 3 posts up. Haha

---

### Post by inyoka on 2010-07-04
Just run 

```
uname -m
```

If it says x86_64 your on 64bit hardware, others like x86 or i686 are 32bit.

---

### Post by abble455 on 2010-07-16
Ok, now I'm confused.

After running
```
$ grep lm /proc/cpuinfo
```I got:
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx**[COLOR=Red] lm[/COLOR]** constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_**[COLOR=Red]lm[/COLOR]** tpr_shadow vnmi flexpriority
```Leading me to believe my laptop is 64 bit capable.

But, after running
```
$ uname -m
```I got.
```
i686
```...which means I have 32 bit hardware??  I'm confused and curious..

---

### Post by pulpfiction on 2010-07-18
> **abble455 said:**
> Ok, now I'm confused.

After running
```
$ grep lm /proc/cpuinfo
```I got:
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx**[COLOR=Red] lm[/COLOR]** constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_**[COLOR=Red]lm[/COLOR]** tpr_shadow vnmi flexpriority
```Leading me to believe my laptop is 64 bit capable.

But, after running
```
$ uname -m
```I got.
```
i686
```...which means I have 32 bit hardware??  I'm confused and curious..

It means your CPU is 64 bits but your Ubuntu is 32 bits. Nothing wrong, it just means you could install Ubuntu 64 bits if you wanted to.

---

### Post by TheDebianGuy on 2010-11-21
I got the same identicle thing! My PC was bought in 2008, but what i got with it was Windows Vista Home Basic 32bit (nightmare). I get the same results from the commands but i'm running ubuntu 32bit. Does this mean my pc is 64bit??

:popcorn:

BTW: When i boot up it says AMD64, does this mean i download (if it is 64bit) the normal one or the AMD64 one? ty

---

