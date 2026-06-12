---
title: "Octave + MKL = improved performance"
date: 2007-09-18
forum: Education &amp; Science
---

### Post by rlgc79 on 2007-09-18
According to this talk ([http://www.austriangrid.at/symposium/talks/descher.pdf](http://www.austriangrid.at/symposium/talks/descher.pdf)), huge performance gains can be achieved with OCTAVE if it is compiled against MKL. Although not free as in speech, the MKL library is free for noncommercial use. Here is a brief description  

Quote from INTEL
"Intel® Math Kernel Library (Intel® MKL) offers highly optimized, extensively threaded math routines for scientific, engineering, and financial applications that require maximum performance."

You can get it here :[http://www.intel.com/cd/software/products/asmo-na/eng/307757.htm]("http://www.intel.com/cd/software/products/asmo-na/eng/307757.htm")

Here is the necessary steps to compile OCTAVE 

1) Download and install the MKL library. Do not forget to check this link [http://support.intel.com/support/performancetools/libraries/mkl/linux/sb/CS-027208.htm]("http://support.intel.com/support/performancetools/libraries/mkl/linux/sb/CS-027208.htm")
In the following, I assume that you installed it with the standard options (folders etc)

2) Download the source code for octave.

3) "Untar" the file: tar -xfvz <filename>

4) Go to the source code folder

5) ./configure --with-blas='-L/opt/intel/mkl/9.1.023/lib/32/ -lmkl -lpthread'  --with-lapack='-mkl_lapack'

(if you run into run into missing dependencies, you can easily fix them with synaptic)
(If your version of the MKL library is different, change the above line to reflect the location of your version)

6) make
7) make install

Now Octave is ready to rock :guitar:

---

