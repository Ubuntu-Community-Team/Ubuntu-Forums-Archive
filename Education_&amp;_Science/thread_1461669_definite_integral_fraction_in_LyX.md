---
title: "definite integral fraction in LyX"
date: 2010-04-24
forum: Education &amp; Science
---

### Post by nandugopan on 2010-04-24
I am trying to type a report which contains a definite integral fraction. But I just cant get the limits to fall in the proper place. I am attaching the image of the equation herewith.Anyone got any ideas on how to get around this?

---

### Post by epitaph on 2010-04-25
I'm not sure if it helps at all, but the TeX/LaTeX for writing that is pretty standard. I'm not sure how to make it appear properly in LyX, but I believe you can manage to just use proper LaTeX code in it.

```
\frac{\int_{1}^{2}R\left|y\right|dx}{l_m}
```

[IMG]http://chart.apis.google.com/chart?cht=tx&chs=1x0&chf=bg,s,FFFFFF00&chco=000000&chl=\frac{\int_{1}^{2}R\left|y\right|dx}{l_m}[/IMG]

---

### Post by nandugopan on 2010-04-26
Dear epitaph,
Thanks for the reply. But that does not solve the problem. I want the 1 and 2 to apper directly above the integral, and not at the right side of it.:confused:

---

### Post by epitaph on 2010-04-26
Try:

```
\frac{\int\limits_{1}^{2}R\left|y\right|dx}{l_m}
```

[IMG]http://chart.apis.google.com/chart?cht=tx&chs=1x0&chf=bg,s,FFFFFF00&chco=000000&chl=\frac{\int\limits_{1}^{2}R\left|y\right|dx}{l_m}[/IMG]

---

