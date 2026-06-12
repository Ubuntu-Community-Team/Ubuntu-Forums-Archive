---
title: "Maxima - Ordinary differential equation problem"
date: 2012-01-29
forum: Education &amp; Science
---

### Post by errrn on 2012-01-29
Hi,everyone

**I'm trying to solve this: **

(%i1) 'diff(y(t),t)+sin(t+y(t));
                                                      d
(%o1)                      sin(y(t) + t) + -- (y(t))
                                                      dt
**with **

(%i4) desolve(%o1,y(t));
[B]
and this is what I get:
[/B]
                          laplace(sin(y(t) + t), t, g33168) - 1
(%o4)   y(t) = ilt(- -------------------------------------, g33168, t)
                                    g33168

ilt being inverse laplace transform. I though it should be able to calculate it, and give me a proper symbolic result, but no.

any ideas? I also tryied with ode2 but I had no luck either.

thanks in advance!

PS: I'm running 11.10, and maxima 5.24

---

