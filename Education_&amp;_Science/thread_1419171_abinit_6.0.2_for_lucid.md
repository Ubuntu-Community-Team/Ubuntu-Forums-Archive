---
title: "abinit 6.0.2 for lucid"
date: 2010-03-01
forum: Education &amp; Science
---

### Post by Yoshis88 on 2010-03-01
Dear Ubuntu,

I know that abinit 5.3.4 is available from the repositories.  From the looks of it, I'm not convinced it got an update since hardy.  Which is fine, unless there are major structural changes, as is the case with the hours-old (as of time of writing) abinit 6.0.2.  I'd like to see this new package available from the repositories.

So, I ask the question:  What can I do to help?  Is it too late in the lucid development cycle?  Or can it still be added or added to an updates repository?  I have sufficient skill to compile it, but I'm not sure what I need to do to make a *.deb or whatever needed for the repositories.  Also, I'd like to see parallel capabilities added to the ubuntu version.  I know the gromacs software has multiple packages that can be installed depending on which MPI framework you use.

---

### Post by Yoshis88 on 2010-03-02
I'm probably just posting this for my own reference, but using the steps below with the 6.0.2 tarball, I'm able to get a working installation with basically all the stops pulled out from everything that can be found in Ubuntu repositories.  Most of it is useless from the point of computational performance. This install it with OpenMPI used.


```
sudo apt-get install g++ gfortran mpi-default-bin mpi-default-dev libblas-dev liblapack-dev libscalapack-mpi1 fftw-dev gawk texlive-latex-base texlive-base-bin texlive-extra-utils markdown python-dev bzr python-numpy

./configure CC=mpicc CXX=mpicxx FC=mpif90 --enable-gsl --enable-fftw-threads --with-fftw-libs=-lfftw_threads --enable-scalapack

make
```

---

### Post by emuller on 2010-03-17
Yoshis,
  Thanks for your post.  I've been having trouble installing abinit 6.02.  I am trying to install it on a relatively clean install of ubuntu 9.10.  I have previously installed abinit 5.8.4, serial only on this machine, and I've installed abinit 5.6 in parallel on an older version of ubuntu and a different machine.  I currently have gfortran and other essentials installed on my current machine (for 5.8.4).  I have tried installing 6.02 using your code, resulting in the following error after typing make:
......
A bunch of good output
......
wannier90-1.1 has been built.
cp wannier90-1.1/wannier90.x wannier90-1.1/libwannier.a .
touch install-stamp
wannier90-1.1 has been installed in tmp.
wannier90-1.1 is now ready for use.
make[4]: Leaving directory `/usr/local/bin/abinit-6.0.2/plugins/wannier90'
if test -d tmp/bin; then mv tmp/bin/* .; fi
if test -d tmp/lib/finclude ; then mv tmp/lib/finclude/* .; rm -rf tmp/lib/finclude; fi
if test -d tmp/lib; then mv tmp/lib/* .; fi
if test -d tmp/include; then 	  find tmp/include -name '*.mod' -exec mv {} . \; ; 	 fi
if test -d tmp/include ; then mv tmp/include/* .; fi
if test -d tmp/finclude ; then mv tmp/finclude/* .; fi
make[3]: Leaving directory `/usr/local/bin/abinit-6.0.2/plugins/wannier90'
make[3]: Entering directory `/usr/local/bin/abinit-6.0.2/plugins'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/local/bin/abinit-6.0.2/plugins'
make[2]: Leaving directory `/usr/local/bin/abinit-6.0.2/plugins'
Making all in src
make[2]: Entering directory `/usr/local/bin/abinit-6.0.2/src'
Making all in incs
make[3]: Entering directory `/usr/local/bin/abinit-6.0.2/src/incs'
There is no buildable file here
make[3]: Leaving directory `/usr/local/bin/abinit-6.0.2/src/incs'
Making all in mods
make[3]: Entering directory `/usr/local/bin/abinit-6.0.2/src/mods'
There is no buildable file here
make[3]: Leaving directory `/usr/local/bin/abinit-6.0.2/src/mods'
Making all in 01_gsl_ext
make[3]: Entering directory `/usr/local/bin/abinit-6.0.2/src/01_gsl_ext'
mpicc -DHAVE_CONFIG_H -I. -I../.. -I../../src/incs -I../../src/incs    -g  -O2   -MT gsl_f90_sf_bessel_j0.o -MD -MP -MF .deps/gsl_f90_sf_bessel_j0.Tpo -c -o gsl_f90_sf_bessel_j0.o gsl_f90_sf_bessel_j0.c
gsl_f90_sf_bessel_j0.c:5:31: error: gsl/gsl_sf_bessel.h: No such file or directory
make[3]: *** [gsl_f90_sf_bessel_j0.o] Error 1
make[3]: Leaving directory `/usr/local/bin/abinit-6.0.2/src/01_gsl_ext'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/bin/abinit-6.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/bin/abinit-6.0.2'
make: *** [all] Error 2


......

I am not sure what to make of this, other than that the install failed.  Thoughts or suggestions?

---

