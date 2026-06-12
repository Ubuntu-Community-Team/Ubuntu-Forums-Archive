---
title: "MathCad integral help :)"
date: 2008-05-05
forum: Education &amp; Science
---

### Post by qbox on 2008-05-05
Hi
I try to use for the first time MathCad 2000 to calculate one integral for school. i need to calculate this integral somehow Symbolic with MathCad
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68898&stc=1&d=1210008741[/IMG]
I do Symbolic->Evaluate->Symbolically
and I receive this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68899&stc=1&d=1210008741[/IMG]
I dont know this is right result or its wrong?
i didnt expect erf(pi) to show up.:confused::confused::confused:
Can same one tell me if Im right or im wrong?
And if I select variable "x" and I do Symbolic->Variable->Integrate
i have this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68900&stc=1&d=1210008741[/IMG]

Please if anyone know to work with MathCad, please tell me if Im wrong and If im right and what to do.
thx

---

### Post by Lux Perpetua on 2008-05-07
I hate to be the one to tell you this, but I believe that your integral has no analytic solution. The integral from 0 to infinity of e^(-x^2) does have an analytic solution, namely sqrt(pi)/2, but I don't think there is such a result for the integral from 0 to pi. 

By the way, see this Mathworld article for the definition of erf: [the "error function"](http://mathworld.wolfram.com/Erf.html) (Mathworld) 

As you can see, sqrt(pi)/2*erf(pi) is indeed equal to your integral, basically by definition.

---

### Post by qbox on 2008-05-14
Thanks. That help me to figure out.:guitar:

---

