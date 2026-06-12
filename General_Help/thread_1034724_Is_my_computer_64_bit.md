---
title: "Is my computer 64 bit?"
date: 2009-01-09
forum: General Help
---

### Post by ivikas on 2009-01-09
Hello all,

         I don't understand my system configuration.I just want to know whether my system is 64 bit or 32 bit.Is dual core 64 bit machines?.And what does i386 or i686 or ppc mean? If my system is 64 bit,then installing a 64 bit ubuntu will speed up performance of my computer,like faster booting,fast program loading and so on.

Please advice ,iam putting  down my system configuration which is as shown by sysinfo

```

CPU Information

	Vendor 		:GenuineIntel
	CPUs		:2
	Model Name	:Intel(R) Core(TM)2 CPU 6320  @ 1.86GHz
	Frequency	:1862.000 MHz
	L2 Cache	:4096 KB
	
More Details
	
	Bogomips	:3732.72
	Numbering	:family(6) model(15) stepping(6)
	Flags		:fpu vme de pse tsc msr pae mce cx8 
                        apic sep mtrr pge mca cmov pat pse36
                        clflush dts acpi mmx fxsr sse sse2 ss
                        ht tm pbe nx lm constant_tsc arch_perfmon
                        pebs bts pni monitor ds_cpl vmx est 
                        tm2 ssse3 cx16 xtpr lahf_lm


```

Thanks in advance

---

### Post by Ripose on 2009-01-09
Yes it is 64 bit.
I386 is basically for 32 bit Intels (or compatible).
PPC is only for Power PC's

Use the I686 Ubuntu or one which specifically states it is for 64 bit systems.

Install SYSTEM MONITOR to get quick very basic info about your PC.

---

### Post by mssever on 2009-01-09
Most, if not all, multi-core CPUs are 64-bit. But that doesn't necessarily mean that you should install the 64-bit Ubuntu.

You won't really gain any noticeable benefits from 64-bit unless you have more than 4 GB of RAM. However, some software still has trouble in 64-bit (though that problem is much less these days).

Personally, I run 32-bit so I can cache my updates and install them on my server which only has a 32-bit processor without having to use extra bandwidth to download the updates.

---

