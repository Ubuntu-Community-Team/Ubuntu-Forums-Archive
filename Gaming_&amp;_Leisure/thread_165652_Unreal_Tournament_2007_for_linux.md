---
title: "Unreal Tournament 2007 for linux?"
date: 2006-04-24
forum: Gaming &amp; Leisure
---

### Post by solarwind on 2006-04-24
I'm sure hoping that there will be a linux release for Unreal Tournament 2007. Anyway, the game seems more complex compared to previous versions. Some sites anticipate that a really good graphics card, a physics processing unit (yes, a physics processing unit) and a dual or quad core cpu will greatly improve performance. But my question is, why buy a three hundred dollar physics processing unit when you can get a symmetrical multiprocessing machine to the physics. Surely the smp machine will have more uses. And will Linux support the physics processor? Wait, what am I saying? Will Windoze support it? And will they make drivers for linux?

---

### Post by handy on 2006-04-25
UT has traditionaly supported linux.

With the number of linux users growing, why would this change?

As far as the hardware requirements are concerned, the diversity of machines that can & do run linux these days, will mean that their capabilities are also diverse.  Some will, some won't, do whatever...

---

### Post by slavik on 2006-04-25
[QUOTE=solarwind]I'm sure hoping that there will be a linux release for Unreal Tournament 2007. Anyway, the game seems more complex compared to previous versions. Some sites anticipate that a really good graphics card, a physics processing unit (yes, a physics processing unit) and a dual or quad core cpu will greatly improve performance. But my question is, why buy a three hundred dollar physics processing unit when you can get a symmetrical multiprocessing machine to the physics. Surely the smp machine will have more uses. And will Linux support the physics processor? Wait, what am I saying? Will Windoze support it? And will they make drivers for linux?[/QUOTE]
because the physics unit has physics equations done in hardware ...

for example, consider the follow 2 ways of adding 2 memory locations.

without CPU instruction:
```

mov eax, memory1
mov ebx, memory2
add eax, ebx
mov memory1, eax

```

the above code makes the CPU decode 4 instructions.

Consider the following code with a CPU instruction for adding 2 memory locations
```

add memory1, memory2

```

The only difference is that you are not using CPU registers (eax and ebx) and that the second piece of code decodes only 1 instruction.

This is the difference between CISC and RISC architectures (Complex/Reduced Instruction Set Computing). The first piece of code is what RISC code looks like, second is for CISC. (Even though the second piece of code will actually execute the first piece of code).

Intel and AMD chips are CISC.

In the 1980s there was a system that would do Lisp in hardware. Let's say that at the time, the IBM AT I think it was which didn't do Lisp in hardware would outperform the Lisp system.

VIA built a CPU (Eden I think) that is 1GHz clock and does 128bit RSA (also AES, SHA-1, SHA-256) encryption in hardware. It is 4 times faster at that encryption than a 3GHz Pentium 4.

This is also the reason why GPU have more and more transistors. To do more image manipulating functions in hardware. For example, every vertex in OpenGL is represented by a 4x4 matrix. The simplest algorithm that you can come up with would take 64 calculations for 2 4x4 matrices (using FT, it becomes 4^2.37). But imagine if that was done in hardware (like it is on all modern cards).

I hope you get the idea. :)

---

### Post by Zeroedout on 2006-04-25
[quote=slavik]because the physics unit has physics equations done in hardware ...

for example, consider the follow 2 ways of adding 2 memory locations.........

.......
I hope you get the idea. :)[/quote]

Wow, thank you for the detailed explaination. I've never understood the rational to throwing those concepts to different peices of hardware. (assuming i understood your post properly)

---

### Post by MetalMusicAddict on 2006-04-25
Yea, nice info. I plan on building a new machine when UT2007 comes. No limit on the money.

---

