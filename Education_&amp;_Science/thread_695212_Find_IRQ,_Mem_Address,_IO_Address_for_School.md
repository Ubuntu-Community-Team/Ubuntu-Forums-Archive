---
title: "Find IRQ, Mem Address, I/O Address for School"
date: 2008-02-12
forum: Education &amp; Science
---

### Post by Rhemat on 2008-02-12
Hi Everyone,

  I am taking a college course for Hardware, and the assignment I'm working on now asks me to find the following for IDE/ATAPI controllers and the video card in the computer:
IRQ
Memory Address
DMA
I/O Address
  Now, of course, it's assumed that the student is using a Windows computer (or they use the campus lab, but that is a long drive I can't make right now).  I am searching in Device manager, but I must not understand how they're defined in linux.
  If there is a better way to look, or if there is a translation for what I see under the Advanced tab, I would appreciate the help.

  Thanks in advance.

---

### Post by AudibleAnomaly on 2009-04-18
try ```
lspci -v
```

---

