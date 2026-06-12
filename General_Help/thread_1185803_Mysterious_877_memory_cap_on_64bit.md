---
title: "Mysterious 877 memory cap on 64bit"
date: 2009-06-12
forum: General Help
---

### Post by afrodeity on 2009-06-12
I have a 1Gb DDR2 667 RAM installed on my Ubuntu Hardy 8.04. 

```

afrodeity@afrodeity-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           877        870          7          0          1         89
-/+ buffers/cache:        778         98
Swap:         2565        669       1895
afrodeity@afrodeity-desktop:~$ 

```

which shows 877 total memory available ie. 123 mb missing?

[This posting]("http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf") refers to a similar problem affecting 32bit, 24 and 26 kernels.

Is this the same problem, and what should I do?

---

### Post by gradinaruvasile on 2009-06-12
Do you have onboard graphics?

---

### Post by jerome1232 on 2009-06-12
Along similar lines what does your bios report as total memory.

---

### Post by Sinkingships7 on 2009-06-12
It's probably on-board graphics, which take a set amount of system RAM for rendering memory (post 2). This should be able to be changed from the BIOS (post 3).

---

### Post by afrodeity on 2009-06-12
Will have to restart the computer to check. I've just installed the VIA chrome driver which might make a difference to the graphics but I'm in the middle of an upload at the moment so can't do it all right now. Thanks for being there for me.;)

---

### Post by gradinaruvasile on 2009-06-12
Via chrome is an onboard video card. I have something like it on my comp (dont use it though).

---

### Post by afrodeity on 2009-06-14
Can't see anything in the BIOS. There is a startup message which says something like 967 plus T memory. Is there any way of confirming that VIA is taking some of my RAM?

---

