---
title: "A good non-linear fitting data program?"
date: 2007-11-13
forum: Education &amp; Science
---

### Post by gnusci on 2007-11-13
Hallo every one...

I been looking for a good program to fit some E-V data to the Birch–Murnaghan equation of state without luck... any idea?

Thanks a lot...

---

### Post by kleeman on 2007-11-13
From experience it is better to transform your data first so that the fitting is to a simple function like a polynomial. That equation of state seems to be a function of V^{-2/3} so use that as a dependent variable and then you have a cubic fit problem which is easy.

---

### Post by euler_fan on 2007-11-15
R has some very solid non-linear estimation routines. One of the major packages for it is nlme (non-linear maximum likelihood estimation) it can also do non-linear least squares.

---

### Post by akniss on 2007-11-15
> **euler_fan said:**
> R has some very solid non-linear estimation routines. One of the major packages for it is nlme (non-linear maximum likelihood estimation) it can also do non-linear least squares.

+1 for R.  Check out the 'drc' package.

---

