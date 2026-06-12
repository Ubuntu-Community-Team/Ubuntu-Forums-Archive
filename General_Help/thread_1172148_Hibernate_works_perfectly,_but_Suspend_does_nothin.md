---
title: "Hibernate works perfectly, but Suspend does nothing"
date: 2009-05-28
forum: General Help
---

### Post by Altay_H on 2009-05-28
My install of Ubuntu 9.04 on my desktop computer has a Hibernate option, but no Suspend option. I know the hardware is capable of suspending because it dual boots Windows XP and can Sleep without any problems. Strangely, if I try to run "pm-suspend" from the terminal (as root, or via sudo) it does absolutely nothing. Control returns to me in the terminal (implying that pm-suspend terminated) and everything continues to run. There are no errors or any kind of output whatsoever. Interestingly Hibenate works correctly. Any ideas?

---

### Post by kerry_s on 2009-05-28
sounds like your bios is set to s1/pos instead of s3/str. set it to s3

---

### Post by Altay_H on 2009-05-28
That was the problem. It took me a little while to find the option in my BIOS, but now that's it's set correctly Suspend works perfectly. Thanks very much.

---

