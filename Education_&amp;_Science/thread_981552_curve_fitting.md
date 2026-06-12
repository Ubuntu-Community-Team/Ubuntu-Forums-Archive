---
title: "curve fitting"
date: 2008-11-13
forum: Education &amp; Science
---

### Post by in_flu_ence on 2008-11-13
Hi,

I want to try to find the exponent of an equation y=a(m^b)(n^c)
I know the data points of y with respect to m and n. Is there a software whereby I can easily find the value of a, b and c for the best fitted line?

Thanks.

---

### Post by Shwefty on 2008-11-13
I imagine Octave could do it...a professor of mine described it as "Poor Man's Matlab".  But, I don't know how to use it myself, sorry!

---

### Post by hzambran_cl on 2008-11-14
You could try with R ([http://www.r-project.org/](http://www.r-project.org/)) + the BB package ([http://cran.r-project.org/](http://cran.r-project.org/)), which is suited for folving and optimizing large-scale nonlinear systems.

Cheers,

Mauricio

---

### Post by brunovecchi on 2008-11-14
Qtiplot also has a curve fitting module that has many built-in functions, and you can also add any kind of custom function (a la Origin).

---

### Post by briansers on 2008-11-14
If you have access to it, you can use Mathematica or Maple.

---

### Post by in_flu_ence on 2008-11-15
Thanks all with the options.

---

### Post by jpkotta on 2008-11-15
You can do it with linear regression, which many, many math apps will do.  Of course, the log skews the fit so that small values of m,n have relatively less error than large values.

```
y = a * m^b * n^c
log y = log a + b*log m + c*log n
y' = a' + b*m' + c*n'
y' = [1 m' n']*transpose([a' b c])
```

---

### Post by Rumo on 2008-11-16
Fminsearch and fminbnd are part of the octave-optim package. As the names suggest, these are used to minimize functions.

To fit data in a least squares sense you need to define an appropriate function. So if this is your function:
```
y=a(m^b)(n^c)
```
The function you'd like to minimize is the following (data = y):
```

err=@(p) sum(abs(p(1)*(m^p(2))*(n^p(3)) - data).^2)

```
You can minimize this by:
```

[p_out fval exitflag] =fminsearch(err,[p_1_start p_2_start p_3_start]);

```
Make sure that y, m and n are vectors with all available data points.

I do not know if there is the equivalent of matlab's curve-fitting toolbox and its fit-function for octave, which also provides error margins, confidence intervals, and is usually my choice when it comes to curve fitting.

---

### Post by WW on 2008-11-16
Technical point: you have two independent variables (m and n), so you are fitting a surface, not a curve.

Check out this sight: [http://zunzun.com/](http://zunzun.com/)

In particular, the function you are interested in is here: [http://pythonequations.appspot.com/EquationInterface/3/Miscellaneous/Gary%20Cler%27s%20Custom%20Equation/](http://pythonequations.appspot.com/EquationInterface/3/Miscellaneous/Gary%20Cler%27s%20Custom%20Equation/)

---

### Post by levelup2 on 2008-12-01
Thanks for all your post, I have the same problem and now it has been sorted!

---

