---
title: "I cannot compile the sample size software: STPLAN"
date: 2007-06-19
forum: Education &amp; Science
---

### Post by felixtandt on 2007-06-19
The STPLAN is very powerful for power and sample size calculation.
[http://biostatistics.mdanderson.org/SoftwareDownload/SingleSoftware.aspx?Software_Id=41](http://biostatistics.mdanderson.org/SoftwareDownload/SingleSoftware.aspx?Software_Id=41)

I have tried it under windows. however,
when I try to compile it under ubuntu 7.04 with gfortran 4.1.2, I
failed. following is the information.

sudo make

f95 -O -c aint2.f90
f95 -O -c apoi2.f90
f95 -O -c exp_dead_1.f90
f95 -O -c exp_dead_2.f90
f95 -O -c fint2.f90
f95 -O -c fpoi2.f90
f95 -O -c gen_poisson.f90
f95 -O -c inv_normal.f90
f95 -O -c pint2.f90
f95 -O -c ppoi2.f90
f95 -O -c qint2.f90
f95 -O -c qpoi2.f90
qpoi2.f90: In function 'check_input_values':
qpoi2.f90:473: internal compiler error: in gfc_conv_variable, at
fortran/trans-expr.c:381
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
make: *** [qpoi2.o] Error 1

Can anyone help me to solve this problem?


how to solve this problem?

thank you in advance.

---

