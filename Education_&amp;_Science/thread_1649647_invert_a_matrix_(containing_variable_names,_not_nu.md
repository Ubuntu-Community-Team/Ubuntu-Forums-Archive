---
title: "invert a matrix (containing variable names, not numbers) in R ?"
date: 2010-12-20
forum: Education &amp; Science
---

### Post by PGScooter on 2010-12-20
Hi,

I would like to invert matrices that have variables in them (variables in the algebraic sense -- ie "x", "y" where x and y do not equal anything in particular).

Can I do this in R, or can you only do it for matrices with numbers or variables that are explicitly specified?

I understand why the following does not work, but it shows what I would like to do:

```

firstcol <- c("a","b")
secondcol <- c("c","d")
tog <- cbind(firstcol,secondcol)
solve(tog)
Error in solve.default(tog) : 
  Lapack routine dgesv: system is exactly singular
In addition: Warning message:
In storage.mode(a) <- "double" : NAs introduced by coercion

```

Thank you

---

### Post by Choragos on 2010-12-22
That's probably not possible in R, though I can't say for sure.  It's quite a mathematically difficult problem you pose.  They're all basically recursive solutions to get the inverse of the matrix, so you'd wind up with what could be a horrible formula sitting in each position of the matrix depending on the size.  It's not really a well posed problem.  Maybe if you can say more about the properties of the matrix we can find a closed-form inverse algebraically, but not really in a general case.

---

### Post by PC_load_letter on 2011-01-02
I am not familiar w/ R but you need a symbolic algebra software to do this. I can do it, easily, in SAGE ([www.sagemath.org](www.sagemath.org)) or of course using MAXIMA, maybe also w/ Octave using the symbolic toolkit.

---

### Post by marrabld on 2011-01-02
WxMaxima is a goer. Qtoctave.  if you want some GUIs to help.  Plus they both have some menu scripts to help you get the syntax correct.

---

### Post by euler_fan on 2011-01-04
R does not support symbolic linear algebra nor almost any other symbolic operation.

---

