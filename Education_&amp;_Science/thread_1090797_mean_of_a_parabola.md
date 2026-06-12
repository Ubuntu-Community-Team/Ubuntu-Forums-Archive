---
title: "mean of a parabola"
date: 2009-03-08
forum: Education &amp; Science
---

### Post by in_flu_ence on 2009-03-08
Strangely, I just can't find the method from google how to find a mean value from a parabola?

Any help?

Cheers

---

### Post by WW on 2009-03-08
What do you mean by the "mean value" of a parabola?

---

### Post by gunksta on 2009-03-09
Given that parabola can be defined as:

[INDENT]*y = **a**x2 + **b**x + **c*
[/INDENT]I do not understand what you are looking for.

---

### Post by in_flu_ence on 2009-03-10
Actually I should state that more clearly.

I have a velocity profile that is parabolic in a pipe. I want to find the mean velocity of this profile. How can I do it? I remember that V_mean = something * V_max. 

Any guiding light?

Cheers

---

### Post by WW on 2009-03-10
If your pipe has a circular cross-section, won't you want the mean of a paraboloid, not a parabola?  They are not the same.

Parabola: V_mean = (2/3)*V_max
Paraboloid: V_mean = (1/2)*V_max

---

### Post by jpkotta on 2009-03-14
Basically: 

Integral of (velocity field) * d(area element), over the area of interest, divided by the area.
\int_0^R \int_0^{2\pi} v(r,\theta) r d\theta dr  / (\pi R^2)
with v(r,\theta) presumably something like V_max*(1-a*r^2).

---

### Post by WW on 2009-03-14
> **jpkotta said:**
> Basically: 

Integral of (velocity field) * d(area element), over the area of interest, divided by the area.
\int_0^R \int_0^{2\pi} v(r,\theta) r d\theta dr  / (\pi R^2)
with v(r,\theta) presumably something like V_max*(1-a*r^2).
That's right, and in this context, the velocity is generally zero at the boundary, so v(r,\theta) = V_max*(1 - r^2/R^2).

---

### Post by in_flu_ence on 2009-03-14
Thanks both.

I have gotten it somewhere that say
V_mean = (2/3)* V_max           (laminar)
V_mean = (49/60) * V_max        (Turbulent)

Any idea where this originate from?

Of course jpkotta has the best answer from the mathematical perspective. That's the way for calculating mean.

Cheers

---

