---
title: "DESKTOP EFFECTS stopped working after i installed ATI driver"
date: 2007-06-03
forum: Desktop Environments
---

### Post by Zakk Walid on 2007-06-03
I use Ubuntu 7.04 Feisty. 
Own Radeon 9600. 

I installed my ATI driver, movies work properly. games work properly, 
The only problem I have is my DESKTOP EFFECTS ! 
the don't work anymore. 
what should i do? 

Thanks a lot for the support.

---

### Post by dfreer on 2007-06-03
I think, although not quite sure, this is due to the open-source "radeon" driver supporting AIGLX, but the closed-source "fglrx" driver from ATI not being able to run AIGLX. was the open-source driver not working for you? If you are need to use the fglrx driver, you might need to create a seperate X login for beryl, like compiz used to make everyone do.

---

