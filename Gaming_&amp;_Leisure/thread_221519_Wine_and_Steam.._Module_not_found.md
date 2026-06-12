---
title: "Wine and Steam.. Module not found"
date: 2006-07-23
forum: Gaming &amp; Leisure
---

### Post by prophet11 on 2006-07-23
I installed steam in the defualt dir made by wine but when i try to run steam i get this error 

**"wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found"**

what does this mean?

---

### Post by Sandlst on 2006-08-03
I had this same problem, not sure what causes it, but out of curiosity I tried to ```
ls
```When in the correct directory, and saw no folders/files of any kind.  It may be because I installed a new version of wine while the terminal was still open, try going up a directory and re-entering the correct one, with the commands ```
cd ..
``````
cd Steam
``` If you installed in the default place.  Hope this helps!

---

