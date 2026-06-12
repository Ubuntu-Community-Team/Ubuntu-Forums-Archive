---
title: "Can Ubuntu handle 4 Gigs of RAM?"
date: 2009-01-20
forum: General Help
---

### Post by ww711 on 2009-01-20
I'm running Intrepid Ibex 8.10, on my laptop; HP nx6325, presently it has 1 gig of RAM.

If I order 2x 2gig memory modules, 4 gig in total, can II 8.10 handle this? I'm hoping it can.

Any potential unwanted outcomes that may occur?

---

### Post by Valok on 2009-01-20
As far as I know, if you are using a 64 bit system then it should be able to utilize the whole 4gigs of RAM.  If not, then it might not be able to use all of your RAM.

---

### Post by Titan8990 on 2009-01-20
32bit can see 3.2GB w/o PAE. You can get PAE (only if your motherboard supports it) by installing the ubuntu server kernel or recompiling the desktop kernel. PAE will allow a 32bit OS to see all 4GB of RAM.

---

### Post by ww711 on 2009-01-20
Oh, it's an AMD Semperon 3500+, so it's not a x64.

---

### Post by Titan8990 on 2009-01-20
Check around your BIOS options or manual to see if PAE is available on your board. Also, a board that old may not even take 4GB.

---

### Post by jespdj on 2009-01-20
[PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) is not a BIOS setting. It is a feature of the operating system. You would need Ubuntu with a special kernel that has support for PAE. The kernel that comes with Ubuntu Server has PAE support.

In the BIOS, you should look if it has a **memory remapping** feature. That should be enabled for your 32-bit OS with PAE or your 64-bit OS to be able to use the full 4 GB RAM.

A normal 32-bit OS will not be able to use more than about 3.2 - 3.5 GB of the RAM.

---

### Post by ww711 on 2009-01-20
Ok I guess one extra 2 gig module to supplement my existing 1 gig, taking it up to 3 gig in total, will be optimum.

---

### Post by dcstar on 2009-01-20
> **ww711 said:**
> Oh, it's an AMD Semperon 3500+, so it's not a x64.

It **is** a 64 bit processor.

---

### Post by WatchingThePain on 2009-01-20
It's whatever your mainboard manual says it can hold really. Linux can utilise massive amounts of ram depending on the platform. I think 32 bit is upto 4GB though. you could get more if your os cpu and mainboard is 64bit capable.

---

### Post by todak on 2009-01-20
From Wikipedia: 

The Linux kernel includes full PAE support starting with version 2.6, enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE. As of 2008, many common Linux distributions come with a PAE-enabled kernel as the distribution-specific default. Of course your system board must also be capable of that much memory. Mine is limited to 2 GB.

---

### Post by mempman on 2009-01-20
> **ww711 said:**
> I'm running Intrepid Ibex 8.10, on my laptop; HP nx6325, presently it has 1 gig of RAM.

If I order 2x 2gig memory modules, 4 gig in total, can II 8.10 handle this? I'm hoping it can.

Any potential unwanted outcomes that may occur?


Is your laptop system architecture 64 or 32 bit?  What version of Intrepid Ibex are you using: 32 or 64 bit version?

---

### Post by ww711 on 2009-01-20
> **dcstar said:**
> It **is** a 64 bit processor.
Oh? There's no sticker on the laptop to confirm it's a 64 processor.

Anyway

```
cat proc/cpuinfo
```

gave me

```
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 76
model name	: Mobile AMD Sempron(tm) Processor 3500+
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy
bogomips	: 1595.97
clflush size	: 64
power management: ts fid vid ttp tm stc

```

---

### Post by ww711 on 2009-01-20
> **mempman said:**
> Is your laptop system architecture 64 or 32 bit?  What version of Intrepid Ibex are you using: 32 or 64 bit version?

32 bit.

---

### Post by dcstar on 2009-01-20
> **ww711 said:**
> Oh? There's no sticker on the laptop to confirm it's a 64 processor.
.......

All Semprons are 64 bit (but only with reduced features like single core), the desktop models can be upgraded to fully performing dual core Athlons.

They are basically entry level 64 bit CPUs.

---

### Post by jerome1232 on 2009-01-20
> **ww711 said:**
> 
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp [COLOR="Red"]lm[/COLOR] 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy
[/CODE]

Who needs a sticker, if you have the lm flag (long mode) then your cpu is 64 bit.

---

### Post by Maheriano on 2009-01-20
I could be mistaken but I saw on a product somewhere (I think it was a box of RAM) that 64 bit Linux and 64 bit Vista Ultimate will handle 128 gigs of RAM each and then down from there respectively with their lower counterparts with most being 4 or 8.

---

### Post by ww711 on 2009-01-20
> **jerome1232 said:**
> Who needs a sticker, if you have the lm flag (long mode) then your cpu is 64 bit.

Never knew that, useful info.

---

### Post by Tomcatt on 2009-10-29
So, where can I find a step by step guide setting up my system for 4gigs of RAM?

Here's what I'm working with:

processor	: 0 & 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T7600  @ 2.33GHz
stepping	: 6
cpu MHz		: 1000.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4656.78
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by tornadof3 on 2009-10-29
Well, unless you have some particularly unusual set-up, you shouldn't really need to do anything special.

step 1 - check that there is no hardware reason why your motherboard will reject 4GB of RAM
step 2 - physically install the RAM
step 3 - check you're running a 64bit linux OS (if not, why not download 64bit Ubuntu 9.10 in about 2 hours...)

and if you're not running 64 bit linux and don't want to do a re-install, have a look at the 32bit "PAE" option talked about earlier in the forum.

---

### Post by darkksyde on 2009-10-29
Ubuntu can support 4gb by using the 64bit or PAE kernel

---

### Post by cascade9 on 2009-10-29
> **dcstar said:**
> All Semprons are 64 bit (but only with reduced features like single core), the desktop models can be upgraded to fully performing dual core Athlons.

They are basically entry level 64 bit CPUs.

Wrong. The OPs +3500 is 64, your right there, but Semprons also came in 32bit (all the old socket a semprons) and in dual-core as well.

---

### Post by pricetech on 2009-10-29
> **ww711 said:**
> Ok I guess one extra 2 gig module to supplement my existing 1 gig, taking it up to 3 gig in total, will be optimum.

No it won't.  Most newer computers use RAM in such a fashion that both sticks are addressed at the same time.  (I know what it's called, the term escapes me right now)  So if you put two sticks that are not the same size, that addressing scheme won't work and, at best, you'll slow your computer down because it won't be able to use that advanced method of accessing RAM.

It looks like your on the 64 bit path from your later posts so this probably becomes irrelevant, but I'm posting it just in case.

---

### Post by Tomcatt on 2009-10-29
I'll play with it after I upgrade Ubuntu to 9.10.  

2 hours, eh?  And I was looking for it early this morning but it wasn't ready.

---

