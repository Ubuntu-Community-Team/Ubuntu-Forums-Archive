---
title: "Is it possible to resume compiling after computer freeze?"
date: 2008-12-12
forum: General Help
---

### Post by Brachabre on 2008-12-12
Can I resume compiling a program (which takes several hours) even after my computer froze? (It was Sage Math program btw) Thanks!

---

### Post by mc4man on 2008-12-12
Note that I've never had a 'crash' while building but in general when a make errors, after resolving the issue, I do a make clean and start over. 

I have several times though resumed a failed make with no issues. If I had a crash I'd probably start over but if the make was well advanced curiosity would force me to resume it.

If it succeeded and if possible (usually is), I'd run the app out of the build folder and see if it worked correctly before doing a make install.

---

