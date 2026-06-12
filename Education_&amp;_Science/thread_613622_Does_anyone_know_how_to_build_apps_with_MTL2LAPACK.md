---
title: "Does anyone know how to build apps with MTL2LAPACK"
date: 2007-11-15
forum: Education &amp; Science
---

### Post by MagiSu on 2007-11-15
I am programming using MTL 2, downloaded from osl.iu.edu. And I've also installed the LAPACK3 library package from APTITUDE. Then, I configured the MTL2 with following commands:

./configure --with-lapack="-llapack -lblas -lg2c"

the ./configure cannot find blas, which I cannot found in APTITUDE. however, I continuede the installation. Now the MTL is usable, but when compiling application, it cannot found LAPACK library. What can I do about this?

---

