---
title: "what family are centrino processors in?"
date: 2009-05-10
forum: General Help
---

### Post by Meow27 on 2009-05-10
im experimenting with kernel compilation, one of the things i want to try out, is optimising my cpu (im sure i wont see any difference, but i still wanna try it )

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.73GHz
stepping	: 8
cpu MHz		: 800.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips	: 1596.44
clflush size	: 64
power management:


```
```
Processor family
  1. 386 (M386)
  2. 486 (M486)
  3. 586/K5/5x86/6x86/6x86MX (M586)
  4. Pentium-Classic (M586TSC)
  5. Pentium-MMX (M586MMX)
> 6. Pentium-Pro (M686)
  7. Pentium-II/Celeron(pre-Coppermine) (MPENTIUMII)
  8. Pentium-III/Celeron(Coppermine)/Pentium-III Xeon (MPENTIUMIII)
  9. Pentium M (MPENTIUMM) (NEW)
  10. Pentium-4/Celeron(P4-based)/Pentium-4 M/older Xeon (MPENTIUM4)
  11. K6/K6-II/K6-III (MK6)
  12. Athlon/Duron/K7 (MK7)
  13. Opteron/Athlon64/Hammer/K8 (MK8)
  14. Crusoe (MCRUSOE)
  15. Efficeon (MEFFICEON)
  16. Winchip-C6 (MWINCHIPC6)
  17. Winchip-2/Winchip-2A/Winchip-3 (MWINCHIP3D)
  18. GeodeGX1 (MGEODEGX1)
  19. Geode GX/LX (MGEODE_LX)
  20. CyrixIII/VIA-C3 (MCYRIXIII)
  21. VIA C3-2 (Nehemiah) (MVIAC3_2)
  22. VIA C7 (MVIAC7)
  23. Core 2/newer Xeon (MCORE2)

```

as you can see im confused as to whether my cpu is labeled under '6' or '9'

can someone please tell me which number i should set my cpu under?

thanks

edit- i forgot to mention im using a centrino cpu (this is a laptop)

---

### Post by hansdown on 2009-05-10
Hi Meow27.

[http://www.google.ca/search?q=centrino+processors&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=centrino+processors&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

The wikapedia article is interesting.

---

### Post by Meow27 on 2009-05-10
the wikipedia article is also not specific. i made a thread here for *help* not for flames.

why is it so hard to comprehend that?!

---

### Post by BslBryan on 2009-05-10
Hello, Meow27. :-)

Firstly, no need to be rude, he wasn't flaming you, he was probably just stumped and trying to help to the best of his ability. :P

Anyway, after a bit of research, it seems that the Centrino processors are in the processor family of their own (CENTRINO).  This is not listed, obviously, in the CPU info.  

It does say, though, under MPENTIUMM, (NEW).  This makes me lean a bit towards that.  However, as I'm not familiar with that family, after telling me your processor, I believed it was M686.

So, I'm stumped as well.  If you want an educated guess, though, or want what I would go with, I would think it was MPENTIUMM.

I hope I've been of at least some help to you.

Best to you, and good luck.

---

### Post by Yellow Pasque on 2009-05-10
Use 9 (Pentium M)
"Centrino" is a marketing term to brainwash people into requesting a Centrino system  by name and convincing OEM's to use Intel parts (CPU, chipset, wireless) so they can slap a "Centrino" sticker on their machine. The term has been used for several years and doesn't denote a specific processor family.

---

### Post by hansdown on 2009-05-10
Just trying to help Meow27.

The wikipedia article says what Temüjin just told you.

---

### Post by todak on 2009-05-10
You have a Pentium M. The "M" designation is for mobile (e.g., laptop) use. The M processor dies are soldered directly to the motherboard, not encased in a ceramic package and plugged into a socket as in desktop/server models as this saves space. Most laptops get VERY warm to the touch, as the lower part of the laptop case is used as the heatsink, which ironically limits its use as a 'Laptop"! :P

---

