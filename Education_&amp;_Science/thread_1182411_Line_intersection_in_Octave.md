---
title: "Line intersection in Octave"
date: 2009-06-08
forum: Education &amp; Science
---

### Post by rasungod_7 on 2009-06-08
Hi,

I am doing very simple graphs of multiple lines, and I am trying to find their intersection, and I am hoping to get both the x and y coordinate. 

If I were doing it by hand, I would set the two equations equal to each other and solve for their common variable, then plug the number back into one of the equations to find other variable.

I couldn't find a command that would do this, can anyone help me?

Thank you,

Rasungod_7

---

### Post by superdan006 on 2009-06-09
Are you familiar with any linear algebra?

If so, you want to solve a system of equations and although I do not know one specific command, you can get the computer to do the math for you.

This guide is very simple to follow even if you've never heard of linear algebra. You can give it a try and see what it does for you.

[http://www.digitalhermit.com/math/Math_Applications_html/node9.html](http://www.digitalhermit.com/math/Math_Applications_html/node9.html)

If you go to the very bottom of the link, it tells you how to do it in one step. Make sure you have entered A and B properly!

-Dan

PS. Illustration of the math you are doing in one line. A is an nxn matrix and B is a column vector:
AX=B => A^-1*AX=A^-1*B => X=A^-1*B

where X will be a column vector representing the coordinates of the intersection.

---

