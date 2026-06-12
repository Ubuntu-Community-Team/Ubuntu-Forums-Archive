---
title: "beryl problem"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by Lise on 2007-04-22
Hey, 

I installed Beryl, but now I can't get the cube anymore and sometimes he reacts very slow 
Somebody knows how to solve this?

---

### Post by Lise on 2007-04-22
> **Lise said:**
> Hey, 

I installed Beryl, but now I can't get the cube anymore and sometimes he reacts very slow 
Somebody knows how to solve this?

I've solved the problem, it was a conflict between my ati card and the xserver-xorg configuration (AIXGL), I switched again to the default configuration and Beryl works again

:) :)

---

### Post by Dorsai on 2007-04-22
> **Lise said:**
> I've solved the problem, it was a conflict between my ati card and the xserver-xorg configuration (AIXGL), I switched again to the default configuration and Beryl works again

:) :)

Could you be more specific about what the "conflict" was and how you fixed it ?

---

### Post by Lise on 2007-04-25
> **Dorsai said:**
> Could you be more specific about what the "conflict" was and how you fixed it ?

I did dpkg-reconfigure xserver-xorg in the terminal ... and after that it worked again. But now I have the same  again, so that's probably not the only problem.

---

