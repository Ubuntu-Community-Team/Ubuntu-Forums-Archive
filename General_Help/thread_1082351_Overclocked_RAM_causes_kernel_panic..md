---
title: "Overclocked RAM causes kernel panic."
date: 2009-02-27
forum: General Help
---

### Post by valros on 2009-02-27
Ok so when setting my memory speed from Auto to 533MHz in the BIOS, Ubuntu(64 bit) then boots straight into a kernel panic. Anyone have any insight on this?

The board is M3A78 from ASUS
AMD 9850 BE
4gb DDR 2 G-Skill memory

---

### Post by jwbrase on 2009-02-27
Someone that's into overclocking might be able to give you a bit more help, but as a general rule, you can't be sure that overclocked components will function properly. That's why it's called overclocking, you're running it beyond the performance range within which the manufacturer is willing to guarantee that it will work. If it does, great. If it doesn't, you've found out what your hardware's limits are.

---

### Post by valros on 2009-02-27
This seems like an odd scenario to me, for one XP boots with it on and the panic comes so consistently, as if Linux gets confused when it sees the ram speed is different.

---

### Post by yther on 2009-02-27
@jwbrase, that statement is true in general.  However, G.Skill tends to make memory that overclocks well, also I think that ASUS board is designed for overclocking and such tweaks.  So, while we can't rule it out, it's less likely in this situation than in others.  :)

I'm not an expert, but **valros**, have you tried checking in XP with a utility like CPUID, to see exactly what the timings are in XP?  I recall that some BIOS allow the OS to change timings dynamically, and I think makers like Gigabyte and ASUS often supply software that does this, so I wonder if perhaps something is getting adjusted automatically.  If that's the case, I bet the same auto-adjustment isn't possible (or isn't being done) in Linux.  It might also show you the specific timings so you can double-check them.

Just because XP works, however, doesn't mean Linux will.  It doesn't mean it *can't*, either.  ;)  You may be able to tweak the memory timings until you find a set that both operating systems can tolerate.  Have you tried searching the web for that board, that memory, or both, and throwing in words like "Linux" or "Ubuntu"?  Maybe someone has encountered a similar problem before.  You might also see if NewEgg.com sells that memory, and if so you can search customer reviews to see if anyone mentions a problem like this.  Overclockers love to talk about their skills, you know, and I came across things like that in reviews while researching some recent purchases.

Good luck!

---

### Post by valros on 2009-02-28
Hrm, found this out from memtest 86, RAM is fine under 400MHz but when taken to 533 memtest starts throwing up all kinds of errors. Motherboard or memory fault?

---

### Post by dcstar on 2009-02-28
> **valros said:**
> Hrm, found this out from memtest 86, RAM is fine under 400MHz but when taken to 533 memtest starts throwing up all kinds of errors. Motherboard or memory fault?

There is no "fault", you cannot run that RAM at that speed.

---

### Post by valros on 2009-02-28
That shouldnt be true in any way though, this was all designed for it, does it matter which slots the memory cards are in?

---

