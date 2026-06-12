---
title: "low graphics mode after 14.04 upgrade"
date: 2014-05-09
forum: Desktop Environments
---

### Post by robertasbalt on 2014-05-09
I have upgraded my ubuntu from 13.10 to 14.04 and after upgrade when I start my laptop pops up a table it says "The system is running in low-graphics mode. Your screen,graphics card, and input device settings could not be detected correctly. You will need to configure these yourself. "I tried to do a lot of things from other old post that people suggest how to fix it but nothing that I have tried works.

---

### Post by kc1di on 2014-05-09
What video card does this machine use?
you may need to install drivers for it. 

If you don't know which card it is post the output of ```
lspci | grep VGA
```

---

### Post by JonPaul on 2014-05-09
same problem. I replaced lightdm with gdm and it came up fine. probably not the best solution but when I posted querying this no one responded....
mdm works too (from noobslab)

during the upgrade there were several files (I can't remember the names) where it asked whether I wanted to keep the original or replace with the new. I suspect I answered wrong on one of these....

---

