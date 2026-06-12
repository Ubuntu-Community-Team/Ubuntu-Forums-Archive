---
title: "how do I manipulate matrices in C++?"
date: 2006-12-16
forum: Education &amp; Science
---

### Post by castudil on 2006-12-16
HI!

I want to manipulate matrices in C++.

GSL is excellent but is in C, I cannot take full advantage of the OO unless I encapsulate the code.  is there something similar to GSL for C++?

---

### Post by mips on 2006-12-16
Stupid question but have you tried to google- 'matrices C++' 

I do not really have an answer though.

---

### Post by hod139 on 2006-12-18
The simplest library I know of is Simple Vector Library [(SVL),]("http://www.cs.cmu.edu/%7Eajw/doc/svl.html") but it has limited functionality.   For more functionality there is Vector Library ([VL]("http://www.cs.cmu.edu/%7Eajw/doc/vl.html")).  More complex, but even more feature rich there is [boost::ublas]("http://www.boost.org/libs/numeric/ublas/doc/index.htm").  Another option is [NewMat,]("http://www.robertnz.net/nm_intro.htm") but I'm not very familiar with that one.

You might have more feedback asking a mod to move this to the programming talk sub-forum.

---

### Post by neoflight on 2006-12-19
open up synaptic and install libnewmat10, and dev OR

```
sudo aptitude install libnewmat10 libnewmat10-dev
```

from synaptic: > Newmat supports matrix types: Matrix (rectangular matrix); UpperTriangularMatrix; LowerTriangularMatrix; DiagonalMatrix;
SymmetricMatrix; BandMatrix; UpperBandMatrix; LowerBandMatrix;
SymmetricBandMatrix; IdentityMatrix;
RowVector; ColumnVector.

Only one element type (float or double) is supported.

The library includes the operations *, +, -, *=, +=, -=, Kronecker product,
Schur product, concatenation, inverse, transpose, conversion between types,
submatrix, determinant, Cholesky decomposition, QR triangularisation,
singular value decomposition, eigenvalues of a symmetric matrix, sorting,
fast Fourier and trig. transforms and printing.

then use the libs as necessary...excellent documentation provided in newmat website...[sos: google]

---

### Post by kleeman on 2006-12-20
If you are very serious about this I recommend you learn Fortran (not hard) and use the blas optimized libraries from intel and AMD. Example:

[http://developer.amd.com/acml.jsp](http://developer.amd.com/acml.jsp)

---

### Post by castudil on 2006-12-20
> **neoflight said:**
> open up synaptic and install libnewmat10, and dev OR

```
sudo aptitude install libnewmat10 libnewmat10-dev
```

from synaptic: 

then use the libs as necessary...excellent documentation provided in newmat website...[sos: google]


thank you, I think this is what I am looking for. eigenvalues, eigenvectors, inverse , det, is basically what I need.

---

