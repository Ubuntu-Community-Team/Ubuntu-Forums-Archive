---
title: "FGLRX same as AIGLX?"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by Cygoku on 2008-01-04
Is it true that FGLRX is the same of the driver and that AIGLX is the name of the technology used?

Cygoku

---

### Post by Mr Greencastle on 2008-01-04
Fglrx is the name of the proprietary driver for ATI cards made by AMD/ATI.
AIGLX is the name of the technology used to have 3d effects. It is built into Xorg now.

Hope that clarifies it a bit, anyone want to elaborate and make it clearer?

Mr Green

---

### Post by PinkFloyd102489 on 2008-01-04
Basically, it's the difference between the Nvidia driver available in the repos and the one from the Nvidia site.

---

### Post by Mr Greencastle on 2008-01-04
> **PinkFloyd102489 said:**
> Basically, it's the difference between the Nvidia driver available in the repos and the one from the Nvidia site.
Except that Fglrx is ATI technology not Nvidia, don't think the Nvidia guys would make crap like that =P

Mr Green

---

### Post by Saint Angeles on 2008-01-04
> **PinkFloyd102489 said:**
> Basically, it's the difference between the Nvidia driver available in the repos and the one from the Nvidia site.
no... fglrx is the Proprietary ATI driver... it doesn't matter which version...

AIGLX is an alternative to XGL for compositing 3d effects.

I use FGLRX and AIGLX and it is good to me.

---

### Post by Cygoku on 2008-01-05
How do I knw if I am running FGLRX or AIGLX?

Cygoku

---

### Post by FuturePilot on 2008-01-05
Yes AIGLX is part of the technology used for compositing.
You can read more on Accelerated Indirect GLX [here]("http://en.wikipedia.org/wiki/AIGLX")

> **PinkFloyd102489 said:**
> Basically, it's the difference between the Nvidia driver available in the repos and the one from the Nvidia site.
There is no difference between the Nvidia driver in the repos and the one from Nvidia's site.

> **Cygoku said:**
> How do I knw if I am running FGLRX or AIGLX?

Cygoku

If you have an ATI card and have installed the Restricted driver for it, you are most likely using the FGLRX driver.  Regardless of what driver you are using you are utilizing some portion of AIGLX

---

