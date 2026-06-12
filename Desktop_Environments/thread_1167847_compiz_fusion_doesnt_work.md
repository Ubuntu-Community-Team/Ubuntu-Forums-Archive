---
title: "compiz fusion doesnt work"
date: 2009-05-23
forum: Desktop Environments
---

### Post by Robertmagical on 2009-05-23
[LEFT]Hello! I have installed the ubuntu 9.04, it is very nice and easy to use, then I have installed the compiz-fusion.deb, and something else involved(the deb format package),the ccsm icon appeard on the control panel, but when I click it , nothing happend.  But it really works on ubuntu 8.10, so is that because the compiz-fusion is not the latset version?  
[/LEFT]

---

### Post by Happy_Man on 2009-05-23
Did you install from the repositories?

---

### Post by Robertmagical on 2009-05-23
> **Happy_Man said:**
> Did you install from the repositories?
Thank you Happy_Man,
No, I have downloaded the deb file , and then double click it to install. It works on *INTREPID IBEX. *

---

### Post by Happy_Man on 2009-05-23
Have you installed the proper drivers for your video card? If you have not installed any new drivers since installing, you should do that first.

If you have, then it might be easier to install from the repos. Most likely the .deb you have is not meant to be used on anything other than intrepid ibex.

open a terminal (Applications --> Accessories --> Terminal) and enter the following:

```
sudo apt-get install compizconfig-settings-manager compiz
```

---

### Post by Robertmagical on 2009-05-24
> **Happy_Man said:**
> Have you installed the proper drivers for your video card? If you have not installed any new drivers since installing, you should do that first.

If you have, then it might be easier to install from the repos. Most likely the .deb you have is not meant to be used on anything other than intrepid ibex.

open a terminal (Applications --> Accessories --> Terminal) and enter the following:

```
sudo apt-get install compizconfig-settings-manager compiz
```

Thanks ,Happy_Man, I will try to install from repos. :D

---

