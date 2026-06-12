---
title: "AMD Penom II X3 with unlocked core issue"
date: 2010-10-05
forum: Desktop Environments
---

### Post by TwistedLogic on 2010-10-05
Hi All,

I have a AMD Phenom II X3 processor and a Gigabyte mobo. I was able to successfully unlock the fourth core on this processor and I have been running Windows-7 64bit and ubuntu 10.04 on this machine for some time. 

Yesterday I installed a bunch of pending updates and since then ubuntu only recognizes and uses one of the cores. Below is the output from cat/cpu/procinfo. Please note that Windows 7 is running smoothly and recognizes all the cores.

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 20 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5613.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

I am not sure what I should do to find what is the cause of this problem. Any help is greatly appreciated.

---

### Post by TwistedLogic on 2010-10-05
Flashing my BIOS to the older version has fixed the issue. I am not sure what caused it but now all the cores are being recognized. :)

---

### Post by robert shearer on 2010-10-05
Here....[http://ubuntuforums.org/showpost.php?p=9921065&postcount=7](http://ubuntuforums.org/showpost.php?p=9921065&postcount=7)
explains it well.



are you **really** running 
> Ubuntu Breezy 5.10  on that ??? :-o

---

### Post by TwistedLogic on 2010-10-05
> **robert shearer said:**
> Here....[http://ubuntuforums.org/showpost.php?p=9921065&postcount=7](http://ubuntuforums.org/showpost.php?p=9921065&postcount=7)
explains it well.



are you **really** running 
 on that ??? :-o

No, I am running Ubuntu 10.04.

---

### Post by robert shearer on 2010-10-05
> **TwistedLogic said:**
> No, I am running Ubuntu 10.04.

Yeah, my question was no way serious :)
Just prompted by noticing your profile...

> Join Date: Mar 2006
Location: Minnesota, USA
Beans: 6
Ubuntu Breezy 5.10 

---

### Post by TwistedLogic on 2010-10-06
> **robert shearer said:**
> Yeah, my question was no way serious :)
Just prompted by noticing your profile...

Oh, I have not updated my profile for ages...:) I guess I should do it now.

---

