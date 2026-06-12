---
title: "How do I point Wine to native DLL's?"
date: 2006-12-09
forum: Gaming &amp; Leisure
---

### Post by trommas on 2006-12-09
Hi!

When installing Wine with "Add/Remove application", there is a comment: "Wine can emulate win dll's, but can also use native dll's" I have winxp on a separate partition, how do I tell Wine to use all the native DLL's?

Hopefully I can run more win apps if I could benefit from my native DLL's...

---

### Post by rbprogrammer on 2006-12-09
i was wondering the same thing.  i tried messing around with wine, but i wasn't sure if what i was doing was right......

---

### Post by rbprogrammer on 2007-01-14
no one knows? :(

---

### Post by alinuxfan on 2007-01-14
I know you need to point to them in winecfg somewhere...let me see if I can find where I found out how to do it.
It was on WINEs website

---

### Post by graigsmith on 2007-01-14
well, first off all, copy the DLL files you need off of your windows partition. and put them in your .wine/drive_c/windows/system32   folder.

then run winecfg at the terminal and click libraries.
type in all the dll's you want to override.

click ok. and your done.

---

### Post by trommas on 2007-01-31
Ok, thanks. I'll try it out

---

