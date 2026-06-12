---
title: "gnome halts 8/10 loads"
date: 2005-08-17
forum: Desktop Environments
---

### Post by yeonil on 2005-08-17
Hello, this is very weird problem, everytime i boot i face a lottery, will i see gnome, or only a black screen? ubuntu loads clean, but when it is attempting to change to graphic mode, i have 8/10 chance that i will have to reboot (black screen+nothing helps) 
And
I had the same issue in Windows(loading screen, changing resolution, and bah, black screen, and next time:"we are sorry but windows didn't managed blah blah or sth :P"), so i ... suppose it's not the software (but i'll post here, anyways)

Yeonil

---

### Post by heimo on 2005-08-17
[QUOTE=yeonil]I had the same issue in Windows(loading screen, changing resolution, and bah, black screen, and next time:"we are sorry but windows didn't managed blah blah or sth :P"), so i ... suppose it's not the software (but i'll post here, anyways)
[/QUOTE]

This would be quite obvious, but I'll ask anyway: do you overclock? Try running memtest (I think it's a boot option on grub, at least on Live CD).

---

### Post by yeonil on 2005-08-17
Heh, no i did not overclock anything. but maybe i have bad settings? 
i have AMD Athlon 2000+ working on 1666Mhz  (seems normal, ill check the multipliers and edit) 
GeForce FX 5200... but it is not overclocked, i even added a fan to cool it down more than enough(works fine)
MSI KT4AV is my motherboard
i'll run the test then

Yeonil

---

### Post by yeonil on 2005-08-17
ok, i am bumping the thread with results os my mem scan:
Adress 0000cdfh2a0 @ 205.2MB is altering it's information (errbits: 000080)
what i can do about it?
and i checked the exact settings of my CPU:
Athlon
spread (?)  0.25%
133Mhz, multiplier and rest set to Auto... which gives 1667Mhz
any hope?

Yeonil

---

### Post by heimo on 2005-08-18
[QUOTE=yeonil]ok, i am bumping the thread with results os my mem scan:
Adress 0000cdfh2a0 @ 205.2MB is altering it's information (errbits: 000080)
what i can do about it?
l[/QUOTE]

Replace your memory. If you have multiple modules, it's probably the first one (unless you have smaller than 256MB modules, not likely). Nothing else you can do. If you have memory modules on other computers / can borrow one from a friend, try that first - but in any case, if you can get 512MB or 1GB module, it won't hurt performance. :) Hopefully this ends your random hangups / blakcouts.

---

### Post by yeonil on 2005-08-18
thanks, it will be inevitable, i suppose. I have only 256, so it's the second one, right?(they are paired, so it doesn't matter for me)... I wonder if it will be it. (i have some weird issues with my graphics card recently, but only in 3D... but that is the place where ram is used most, so i have no choice :P (the problem is as follows: playing in a game, or simply using a screensaver with 3D (OpenGL?) results in random moments of halt: there are vertical stripes each 5cm (200px?) layered on the stopped graphics. Then i reboot :P) now thanks to the memtest i have something to blame it on :P )
Hmm is it possible that a address at the end of my RAM makes that booting problems? Hmm. Hmm. Yes its possible :P.
Thanks for help!

Yeonil

---

### Post by heimo on 2005-08-18
Yes if you have two 128MB modules, it's likely the second one that's defective (but to make sure, after swapping bad module out, run the memtest again). It really, really looks like bad memory problem, all those random problems and memtest agreeing with us. You should probably check that memory voltage settings in BIOS are correct / at defaults.

Let us know if it really was bad memory. :)

---

