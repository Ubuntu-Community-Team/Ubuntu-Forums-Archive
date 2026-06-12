---
title: "NVIDIA OpenGL Driver needs SSE capable CPU for most games. Can this be fixed?"
date: 2009-07-08
forum: Gaming &amp; Leisure
---

### Post by anthony62490 on 2009-07-08
ZSNES, Snes9x, most games running under WINE, and practically all of my scene demos require an SSE capable processor. Is this something that can be fixed/downloaded, or do I just need to buy a new CPU? 

If I need to buy a new CPU, what kind would you suggest?

Also, ZSNES ran perfectly fine under 8.10 on the same machine.

---

### Post by Hairybudda on 2009-07-08
cat /proc/cpuinfo and see if sse is listed

---

### Post by ELD on 2009-07-08
SSE is processor level, if you don't have SSE you must have a very old processor? As per the instruction above do that in terminal and look for "flags:" it will be listed after their.

---

### Post by anthony62490 on 2009-07-08
okay, I'm not at my linux computer now, but assuming that SSE is NOT listed, then my CPU is worthless for OpenGL gaming. Can I just take out the CPU of a newer computer and stick it in mine?

---

### Post by Grishka on 2009-07-08
> **anthony62490 said:**
> okay, I'm not at my linux computer now, but assuming that SSE is NOT listed, then my CPU is worthless for OpenGL gaming. Can I just take out the CPU of a newer computer and stick it in mine?

consult the instruction manual for your motherboard to see what CPUs will fit.

---

### Post by Hairybudda on 2009-07-08
> **anthony62490 said:**
> okay, I'm not at my linux computer now, but assuming that SSE is NOT listed, then my CPU is worthless for OpenGL gaming. Can I just take out the CPU of a newer computer and stick it in mine?

If it's an athlon XP/MP it -should- support SSE if i recall correctly

---

### Post by anthony62490 on 2009-07-08
> **Hairybudda said:**
> If it's an athlon XP/MP it -should- support SSE if i recall correctly
Well, my terminal seems to think otherwise.

Also, my computer was a gift. It came with no instructions and no installation disks. I'll check Gigabyte's website and see if they keep old manuals.

---

### Post by BlackRoijaX on 2009-07-08
The fastest single core Athlon is 2.33GHZ, and you say you have a 3GHZ? Is it overclocked or maybe a Athlon x2?

---

### Post by ELD on 2009-07-08
> **BlackRoijaX said:**
> The fastest single core Athlon is 2.33GHZ, and you say you have a 3GHZ? Is it overclocked or maybe a Athlon x2?

Yeah i'm wondering this also.

---

### Post by Hairybudda on 2009-07-08
The Athlon XP/MP range were performance rated rather than actual speed rated, the 3200 barton ran at 2.2ghz iirc, it really should support sse, something must be wrong.

---

### Post by anthony62490 on 2009-07-09
> **BlackRoijaX said:**
> The fastest single core Athlon is 2.33GHZ, and you say you have a 3GHZ? Is it overclocked or maybe a Athlon x2?

Oh, shoot. I think I goofed on the speed. Come to think of it, there's no way my CPU is THAT fast. When I checked the processor speed, I looked at the capacity instead of the size... Sorry about that.

```
sudo lshw -class cpu
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: 6.4.4
       slot: Socket-A
       size: 1333MHz
       capacity: 3GHz <--- hehe, oops.
       width: 32 bits
       clock: 133MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up

```

---

### Post by wingnux on 2009-07-09
You'll need a new processor.

And you don't need wine to run zsnes or snes9x, both have native ports.

---

### Post by anthony62490 on 2009-07-11
> **wingnux said:**
> You'll need a new processor.

And you don't need wine to run zsnes or snes9x, both have native ports.

Haha, I'm not trying to run ZSNES under WINE, but thanks anyway. Just using WINE for my games and my demos.

Yeah, I figured I need a new processor. I'll scrap one of my other computers and see if one of them can play games.

Thanks for your help, everyone.

---

### Post by efikkan on 2009-07-11
If you got a K7 Athlon Thunderbird, then it only supports MMX and 3DNow!
The slightly newer Athlon XP supports SSE.

---

### Post by mister_playboy on 2009-07-20
133MHz?  Now I don't feel so bad when I pull out my laptop with its 400MHz Celeron... :D

---

