---
title: "Recommended Source Please: Least Squares Fit subject to Constraints"
date: 2008-06-27
forum: Education &amp; Science
---

### Post by mj-barton on 2008-06-27
Afternoon all,

I'm looking for a solution to the following problem.

I have a Nx3 matrix, called "XYZ" where the columns represent the x,y, and z axes and the individual row vectors are coordinates in a 3 dimensional space. I'm looking for a way determine the least squares fit plane for that 3D dataset. The tricky thing that I'm hung up on is that the resulting plane must contain a reference point.

Hopefully, a worked solution exists so that I can model it in Octave or Matlab.

Thank you for your time,
Mike.

---

### Post by bite on 2008-06-28
> **mj-barton said:**
> Afternoon all,

I'm looking for a solution to the following problem.

I have a Nx3 matrix, called "XYZ" where the columns represent the x,y, and z axes and the individual row vectors are coordinates in a 3 dimensional space. I'm looking for a way determine the least squares fit plane for that 3D dataset. The tricky thing that I'm hung up on is that the resulting plane must contain a reference point.

Hopefully, a worked solution exists so that I can model it in Octave or Matlab.

Thank you for your time,
Mike.

Simple solution (not accurate if the reference point is very displaced with respect to other points):
determine the least squares plane by singular value decomposition, then translate the plane parallel to itself until it contains the reference point.


Difficult solution (should work always):
Set up an optimum search problem:

minimize Sum_{i=1}^{N-1} (n_x X_i + n_y Y_i + n_z Z_i - d)^2

subject to:
n_x ^ 2 + n_y ^ 2 + n_z ^2 = 1
and to:
n_x X_0 + n_y Y_0 + n_z Z_0 - d = 0

where [X_0 Y_0 Z_0]^T is the point which must exactly lie on the plane,
[X_i Y_i Z_i]^T, i=1..N-1 are the points whose distance to the plane must be minimal,
for a total of N points;
[n_x n_y n_z]^T is the unit vector normal to the plane,
d is the signed distance plane-origin,
^T means "transpose".

This nonlinear problem can be solved with the Lagrange multipliers method. Use Newton-Raphson or better Levenberg-Marquardt to get the numeric result.

EDIT you could also try this one (simpler than last proposed solution).
Express your points in 4-space by adding them a 4th coordinate equal to 1.
The fact that the plane must contain point 0 is expressed by the single equation:
a X_0 + b Y_0 + c Z_0 + d = 0
where a, b, c, d are the unknowns.
This is a system (!) with just one equation. You can decompose it in singular values, anyway. You should get one singular value different from zero and three identically zero or very close to.
The three (out of four) columns of the right unitary matrix coming from the decomposition, which correspond to the null singular values, form a basis of the nullspace of the problem; call them v_1, v_2, v_3 (they are 4-vectors).
So you can express the solution (your plane) as a linear combination: p = c_1 v_1 + c_2 v_2 + c_3 v_3
Now you want to minimize the distances between this parametric plane and points 1..N, that is:
c_1 (v_1 dot [X_i Y_i Z_i 1]) + c_2 (v_2 dot [X_i Y_i Z_i 1]) + c_3 (v_3 dot [X_i Y_i Z_i 1]), i=1, N-1
This homogeneous overdetermined system can in turn be solved by SVD, getting c_1, c_2 and c_3.

---

### Post by bite on 2008-06-28
> **bite said:**
> 
Now you want to minimize the distances between this parametric plane and points 1..N, that is:
c_1 (v_1 dot [X_i Y_i Z_i 1]) + c_2 (v_2 dot [X_i Y_i Z_i 1]) + c_3 (v_3 dot [X_i Y_i Z_i 1]), i=1, N-1
This homogeneous overdetermined system can in turn be solved by SVD, getting c_1, c_2 and c_3.

Mmh, sorry, I see a flaw here... the dot-product I wrote, in 4-space, is not the distance. You should keep into account just the first three components:

c_1 (v_1X X_i + v_1Y Y_i + v_1Z Z_i) + c_2 (v_2X X_i + v_2Y Y_i + v_2Z Z_i) + c_3 (v_3X X_i + v_3Y Y_i + v_3Z Z_i), i=1, N-1

This way it should work.

---

### Post by kleeman on 2008-06-28
Check a comprehensive text on linear algebra. The solution to these problems can almost always be obtained by solving certain matrix equations. You need math not software for these sort of problems imho.

---

### Post by mj-barton on 2008-06-30
> **bite said:**
> Mmh, sorry, I see a flaw here... the dot-product I wrote, in 4-space, is not the distance. You should keep into account just the first three components:

c_1 (v_1X X_i + v_1Y Y_i + v_1Z Z_i) + c_2 (v_2X X_i + v_2Y Y_i + v_2Z Z_i) + c_3 (v_3X X_i + v_3Y Y_i + v_3Z Z_i), i=1, N-1

This way it should work.

Is there a firefox plugin to render the equations you included in your replies?

---

### Post by bite on 2008-07-01
> **mj-barton said:**
> Is there a firefox plugin to render the equations you included in your replies?

No, there is no firefox plugin and also maybe I've been a little bit obscure. :)

But have a look at the attached c++ commented program. It is self-contained, no need for external libraries -- just rename and compile it with

```

mv constrainedLeastSquares.txt constrainedLeastSquares.cpp
g++ constrainedLeastSquares.cpp

```

then

```

./a.out

```

---

