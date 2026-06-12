---
title: "slow matrix multiplication in R (hardy)"
date: 2008-07-12
forum: Education &amp; Science
---

### Post by khosra on 2008-07-12
I am running R on 8.04 on a dual core amd64. Matrix multiplication is extremely slow:
```
> set.seed(123) 
>  X <- matrix(rnorm(1e6), 1000) 
>  system.time(for(i in 1:25) X%*%X) 
   user  system elapsed 
114.667   0.936 118.259 
```
versus the R packaged with the Sage distribution:
```
sage: set.seed(123)
sage: X <- matrix(rnorm(1e6), 1000) 
sage: system.time(for(i in 1:25) X%*%X)
   user  system elapsed 
 17.213   0.308  18.052
```
That's a fair bit slower and I had the same problem with numpy on Hardy and had to rebuild from source.

The problem seems to be that R is not using the blas from atlas.

Hardy:
```
~$ ldd /usr/lib/R/modules/lapack.so
	linux-vdso.so.1 =>  (0x00007fff0c5fe000)
	libR.so => /usr/lib/R/lib/libR.so (0x00007fc003de9000)
	libRlapack.so => /usr/lib/R/lib/libRlapack.so (0x00007fc0039fb000)
	libblas.so.3gf => /usr/lib/libblas.so.3gf (0x00007fc003780000)
	libgfortran.so.2 => /usr/lib/libgfortran.so.2 (0x00007fc0034c1000)
	libm.so.6 => /lib/libm.so.6 (0x00007fc003240000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007fc003031000)
	libc.so.6 => /lib/libc.so.6 (0x00007fc002ccf000)
	libreadline.so.5 => /lib/libreadline.so.5 (0x00007fc002a8f000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007fc002868000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00007fc002658000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007fc002441000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fc00223c000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fc004514000)
	libncurses.so.5 => /lib/libncurses.so.5 (0x00007fc002001000
```
and in the Sage distribution, same machine with atlas3 packages installed:
```
~$ ldd ~/sage/local/lib/R/modules/lapack.so
	linux-vdso.so.1 =>  (0x00007fff44dfe000)
	libR.so => /usr/lib/R/lib/libR.so (0x00007f433c681000)
	liblapack.so => /usr/lib/atlas/liblapack.so (0x00007f433bd29000)
	libcblas.so => /usr/lib/libcblas.so (0x00007f433b403000)
	libf77blas.so => /usr/lib/libf77blas.so (0x00007f433aadc000)
	libatlas.so => /usr/lib/libatlas.so (0x00007f433a175000)
	libm.so.6 => /lib/libm.so.6 (0x00007f4339ef3000)
	libc.so.6 => /lib/libc.so.6 (0x00007f4339b91000)
	libblas.so.3gf => /usr/lib/libblas.so.3gf (0x00007f4339917000)
	libgfortran.so.2 => /usr/lib/libgfortran.so.2 (0x00007f4339657000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f4339449000)
	libreadline.so.5 => /lib/libreadline.so.5 (0x00007f4339209000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007f4338fe2000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00007f4338dd2000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f4338bbb000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f43389b6000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f433ccac000)
	libblas.so.3 => /usr/lib/atlas/libblas.so.3 (0x00007f4338018000)
	libg2c.so.0 => /usr/lib/libg2c.so.0 (0x00007f4337de8000)
	libncurses.so.5 => /lib/libncurses.so.5 (0x00007f4337bac000
```

This keeps coming up again and again. I keep having to recompile stuff from source and it's a little beyond me. Everything I use depends on blas and it seems everything on Hardy is built with a blas that is 5-10x slower and therefore almost unusable. The different options for using lapack, blas, atlas are over my head. I understand there are a set of difficult issues in this area. But I was hoping the default hardy packages would work.

Is there a workaround this problem? Are there alternative repositories for R built with atlas? Are there a set of repositories for ubuntu scientific software that doesn't perform so poorly.

Thanks.

---

### Post by ahmatti on 2008-07-12
> 
Is there a workaround this problem? Are there alternative repositories for R built with atlas? Are there a set of repositories for ubuntu scientific software that doesn't perform so poorly.

Thanks.

I use the AMD Core Math Library (ACML) [http://www.amd.com/acml](http://www.amd.com/acml) (also with amd64 dual core) as described in [http://cran.r-project.org/doc/manuals/R-admin.html#Shared-BLAS](http://cran.r-project.org/doc/manuals/R-admin.html#Shared-BLAS). It gives you roughly the same performance as your sage example.


From the link (with added sudo):
> 
Another option to change the BLAS in use is to symlink a dynamic BLAS library (such as ACML or Goto's) to R_HOME/lib/libRblas.so. For example, just

sudo mv R_HOME/lib/libRblas.so R_HOME/lib/libRblas.so.keep
sudo ln -s /opt/acml4.0.1/gfortran64_mp/lib/libacml_mp.so R_HOME/lib/libRblas.so


In addition you need to run:
sudo ln -s /opt/acml4.1.0/gfortran64_mp/lib/libacml_mv.so R_HOME/lib/libacml_mv.so


Substitute "R_HOME" directory with your R directory, for me it is 
"/usr/local/lib64/R/"

I don't know of any alternative repos R built with atlas, but the above manual provides you a good set of options and instructions for using an optimized blas suitable for your platform.

Using an optimized BLAS gives you a significant speed up in matrix computations, but actually for most of my work it doesn't make any difference. I ran a few of my own benchmarks after changing to optimized blas there was no difference e.g. in fitting AR models or using wavelet operations with wmtsa package ...

---

### Post by rybu on 2008-07-12
What algorithm is being called to perform the matrix multiplication?  Presumably it treats the matrices as "dense" ie: it takes into account every entry, even if it is zero. That's why it's so slow.

BLAS has algorithms to perform faster multiplications but you have to "tell" it what algorithm to use, and there's only a speed-up if your matrix has a particular form.  For example, if you know your matrix has lots of zeros in it, you could re-cast it as a sparse matrix and multiplication will be a fair bit faster, presuming your matrices are large enough. 

Is R supposed to do this kind of thing automatically -- keep a count of the number of non-zero entries in a matrix and then cast it appropriately as a sparse or dense matrix then call the appropriate multiplication algorithm?  If not, you probably also have to "tell" R to consider the matrix to be sparse, or whatever other nice property it has.

I've made some attempts at coding with the BOOST BLAS library but so far I've found it to be rather unpleasant and am considering writing my own sparse matrix library. The library templates are fine if you're using a standard data type like double or int, but I haven't found a way to get it to use things like arbitrary precision integers or reals. It'd also be nice to get it to work with things like interval-arithmatic types...

---

### Post by khosra on 2008-07-12
Thanks ahmatti.

Your suggestion worked very well for a version of R I had already built from source (2.7.1). I replaced the library with the acml as you described and I was able to get faster timings than the sage version. The acml_mp version used both cores whereas the Sage version didn't. (The other version of acml with 64-bit int's coredumped).

However, I didn't try swapping the links in the ubuntu installed package. I am guessing it's libblas.so.3gf that has to be changed. What I did, though, is install libatlas3gf-base ubuntu package and R is now using it and the timing is comparable to Sage. I was using another atlas before. I don't know what the difference is, maybe nothing, but what I had before was probably screwed up in /etc/alternatives.

So these are two solutions. This may resolve my problems with other things such as numpy. It must be a real headache for the maintainers of these packages.

---

### Post by ahmatti on 2008-07-13
You might also want to checkout the "crossprod" function in R and the Matrix package for R h ttp://cran.r-project.org/web/packages/Matrix/index.html. It provides additional functionality (including sparse matrices mentioned by Ruby) for matrix calculations and a nice Vignette with performance comparisons [http://cran.r-project.org/web/packages/Matrix/vignettes/Comparisons.pdf](http://cran.r-project.org/web/packages/Matrix/vignettes/Comparisons.pdf).

---

