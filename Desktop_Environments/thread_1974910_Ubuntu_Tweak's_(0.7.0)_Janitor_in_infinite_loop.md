---
title: "Ubuntu Tweak's (0.7.0) Janitor in infinite loop"
date: 2012-05-06
forum: Desktop Environments
---

### Post by Amalka on 2012-05-06
I've upgraded to 12.04 (from 11.04 over 11.10) and have installed ubuntu tweak. The problem is that when I used janitor function things went smoothly until I tried to clean Apt Cache. Search stops at 3530 items and then stops - or better said stalls - (I guess) in infinite loop; scanning does not complete, hourglass icon is active and there's nothing much to do but to close the program.

Help would be appreciated. :)

---

### Post by Amalka on 2012-05-11
Bump :)

I suppose it is a bug in a program, so there's nothing to do but wait.:popcorn:

---

### Post by wilee-nilee on 2012-05-11
Run this, just copy and paste it if you want, then check the tweak.

```
sudo apt-get autoremove && sudo apt-get autoclean
```

---

### Post by Amalka on 2012-05-11
Hey, that worked great!

Thanks a lot :)

---

### Post by wilee-nilee on 2012-05-11
> **Amalka said:**
> Hey, that worked great!

Thanks a lot :)

I use ubuntu tweak as well, but those two commands clean as well, cool glad it worked. :)

---

