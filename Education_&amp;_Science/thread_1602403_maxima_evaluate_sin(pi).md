---
title: "maxima evaluate sin(pi)"
date: 2010-10-21
forum: Education &amp; Science
---

### Post by Xapati on 2010-10-21
Is there any way to have Maxima simplify trigonometric functions like sin(pi)? Currently when I type in anything like sin(pi) it simply spits out sin(pi) instead of 0. 

The manual mentions that %piargs must be set to true for this to happen, but even when I set it to true Maxima doesn't simplify.

Help would be greatly appreciated.

Edit: Figured it out, put it in as sin(%pi). But I've got a different question, say I have sin(n*pi), and and n is known to be 1,2,3,... is there any way to define n like that so Maxima will simplify sin(n*%pi) to 0?

---

### Post by belanger on 2010-11-14
You've probably gotten the information you need by now, but for those searching the forums:  one thing you can do is declare n to be an integer:
declare(n,integer);

(%i1) sin(n*%pi);
(%o1)                             sin(%pi n)
(%i2) declare(n,integer);
(%o2)                                done
(%i3) sin(n*%pi);
(%o3)                                  0

You could add assume(n>0) if you need to restrict n to the positive integers.

---

