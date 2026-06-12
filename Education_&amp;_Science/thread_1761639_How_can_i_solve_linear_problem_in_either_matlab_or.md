---
title: "How can i solve linear problem in either matlab or c/java?"
date: 2011-05-18
forum: Education &amp; Science
---

### Post by abraxas334 on 2011-05-18
I need to solve a linear set of equations. I have a vector of length n called X. x_1=0 and x_n=1 all other elements are unknown. Furthermore I have a n*n matrix A with row sums to 1. I need to find the missing information in the vector x, through this self consistent definition:

x_i = sum_n A_in*x_n Do this for all i >1 and i<n. I can obviously right my own code in order to do this, but maybe there is a fast existing way on how to solve such a problem. Any help would be appreciated. Thanks

---

### Post by abraxas334 on 2011-05-18
Ok let me reformulate:
I want to solve Ax=x, where A is a square matrix and x a vector of length n, with the information that x_1=0 and x_n=1.
How can I do this in Matlab?

---

### Post by zia.newversion on 2011-05-18
First of all, I am not a mathematician. Just an engineer (student :p).

I don't think Ax=x is the standard form... Perhaps you mean Ax=B.
But after all, Ax=x is same as A1x=0, where A1 is the modified form of A with all diagonal members minus 1.

Once that is settled, for the solution of simultaneous linear equations, there is Cramer's rule, or Jacobi Method... You might know of them already and if you don't please look it up yourself. That is, if you want to solve it using mid-level programming approach (C, Java, etc).

Lastly, if you are looking for a solution in MATLAB, you should see [this]("http://www.mathworks.com/help/techdoc/math/f4-983672.html") section of MATLAB central. (I am sure it is present in MATLAB help as well, in Linear Algebra Toolbox)...

In any case, please post your findings on the thread and don't forget to mark it solved once it indeed is solved. Thank you.

---

### Post by PC_load_letter on 2011-05-18
Ax = x could have many solutions because it's equivalent to solving (A-I)x = 0, so you're trying to find the null space of the matrix A-I, or also equivalently you're trying to find all the eigenvectors corresponding to the eigenvalue 1 if x != 0. 

So look in the Matlab help, or Octave's for commands to find the null space of a matrix or the eigen vectors. I believe there is plenty. 

One question (concern), you have to know what n = ? Matlab or Octave will not be able to solve this aproblem for an arbitrary n.
Also, you have to have all the entries of A, unless you use the symbolic toolkit or something but I'm not sure what you're trying to accomplish here.

---

### Post by abraxas334 on 2011-05-19
Thank you for the input. Yeah I have looked at finding null space.
In matlab/octave its actually just null(A) I have a specific example of a 12x12 matrix. 
What I am not sure of is how to incorporate my boundary conditions of x_0=0 and x_n=1. I guess I wasn't very clear with my question.
Thanks,

---

### Post by abraxas334 on 2011-05-19
I am just silly, from the boundry conditions I can easily construct a solvable system like Ax=b! I was too focused trying to solve for the null space!

---

