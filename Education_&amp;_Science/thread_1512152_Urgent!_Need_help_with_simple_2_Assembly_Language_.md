---
title: "Urgent! Need help with simple 2 Assembly Language tasks"
date: 2010-06-17
forum: Education &amp; Science
---

### Post by AndyBoy_LV on 2010-06-17
Hi everyone!

I`m not really good at Assembly, so i really need some help with this short program. This is a part of my homework :) I`m into web-development (PHP+Stuff), so these low-level languages are a disaster for me... 

Task 1:
Registers R1, R2, ... R7 have numbers 1,2, ... 7 in them. The question is, what will be in these registers after the following part of ARM assembly program has been run:

```

stmfd sp, {r1, r2, r3, r4}
str r5 [sp, #-4]!
sub sp, sp, #8
stmfd sp!, {r6, r7}
ldr r1, [sp]
ldmfd sp!, {r2, r3, r4}
ldr r5, [sp, #4]
ldmfd sp, {r6}
ldmfd sp!, {r7}

```

If somebody would be so kind and help me, please also write some comments so that i can understand what it`s all about...

Task 2:
Write ARM assembly function, that (using a call to printf with a format "%x\n")  prints all "special" natural numbers from 1 to 505356. "Special" means that the sum of pair digits in this number is equal to the sum of unpair digits. For example: 109A (1+9 = 0+A) 

Any help would be appreciated... Big thank you in advance.

---

### Post by gunksta on 2010-06-18
I don't do Assembly.

And, the Ubuntu Forums Code of Conduct does prohibit this sort of activity. I don't know if anyone in this forum uses Assembly. You might have better luck in other sub-forums, but don't ask people to do your homework for you.

---

### Post by ugm6hr on 2010-06-18
> **gunksta said:**
> And, the Ubuntu Forums Code of Conduct does prohibit this sort of activity. 

Indeed. Closed.

---

