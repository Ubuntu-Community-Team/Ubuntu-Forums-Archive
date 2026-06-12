---
title: "[SOLVED] running or uninstalling darwin demo"
date: 2009-02-17
forum: Gaming &amp; Leisure
---

### Post by 21:27 on 2009-02-17
Can't figure this one out. I have Intrepid Ibex. I have installed darwin demo. When I click on the icon, nothing happens. I can't even uninstall it. Have anyone encountered this kind of thing?

EDIT: I mean darwinia. :/

---

### Post by Perfect Storm on 2009-02-17
64-bit user?

---

### Post by 21:27 on 2009-02-17
Yes.

---

### Post by oldrocker99 on 2009-02-17
Install the 32-bit libraries, dude!

:guitar:

---

### Post by 21:27 on 2009-02-18
Well, I installed all the 32 libraries needed for installation. Is there others I need?

---

### Post by Perfect Storm on 2009-02-18
> **21:27 said:**
> Well, I installed all the 32 libraries needed for installation. Is there others I need?

Yes, getting it run on 64-bit is a bit tricky, I wrote this guide for the full game; [http://gaming.gwos.org/doku.php/guides:64bit:darwinia](http://gaming.gwos.org/doku.php/guides:64bit:darwinia)

---

### Post by 21:27 on 2009-02-18
Yes, i have checked that site before and seem to have installed all the listed packages.
Is that the only possible solution?

---

### Post by Perfect Storm on 2009-02-18
Run darwinia from the terminal and see what it says.

EDIT:

Also do this;
```
cd <into darwinia dicrecory>
ldd darwinia.bin.x86
```

---

### Post by 21:27 on 2009-02-18
Yes, I kinda figured it out. So it said I needed a libgcc_s.so.1 Got it with getlibs, but it still didn't run. I tried replacing the libgcc_s.so.1 from darwinia/lib with libgcc_s.so.1 from lib32 and it worked! Thanks for your help.

---

