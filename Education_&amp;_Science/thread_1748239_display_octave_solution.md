---
title: "display octave solution"
date: 2011-05-03
forum: Education &amp; Science
---

### Post by 5argan on 2011-05-03
Hi,

I used octave to calculate the solutions for an equation system.
However, I want it to only print the first solution while printing the second one after displaying a message. Unfortunately, I can only get it to display both solutions at the same time (using disp() or num2str).

---

### Post by normandin on 2011-05-26
The exact syntax will depend on how the solution is stored as a variable. But something analogous to
```
fprintf ('%f\nMessage\n%f\n', x(1), x(2));
```
ought to do what you want.

---

