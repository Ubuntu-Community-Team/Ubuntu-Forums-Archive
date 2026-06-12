---
title: "Build Octave-3.2.0 from source? - make error!! - DapperDrake"
date: 2009-06-30
forum: Education &amp; Science
---

### Post by serxyz on 2009-06-30
Hi all,

I am a regular Matlab user under Ubuntu6-DapperDrake and I want to switch to Octave3. 

I am trying to install it from source by compiling its code ([http://ubuntuforums.org/archive/index.php/t-680690.html](http://ubuntuforums.org/archive/index.php/t-680690.html)). 

I have followed the following steps:

1) I set up the folders from which to install the program:

==========================================
sudo chown username /usr/local/src
sudo chmod u+rwx /usr/local/src

sudo mkdir /usr/local/OCTAVE3p2
sudo chown username:root /usr/local/OCTAVE3p2
sudo chmod u+rwx /usr/local/OCTAVE3p2
==========================================

2) I downloaded ([http://www.gnu.org/software/octave/download.html](http://www.gnu.org/software/octave/download.html)) the stable version "octave-3.2.0.tar.gz" into "/usr/local/src".

3) I extracted the tarball:

==========================================
cd /usr/local/src/
tar xzvf octave-3.2.0.tar.gz
==========================================

4) I installed many things:

==========================================
sudo apt-get build-dep octave

sudo apt-get install g77 
sudo apt-get install f2c
sudo apt-get install fort77
sudo apt-get install gfortran
sudo apt-get install xlibs-dev
sudo apt-get install libx11-dev
sudo apt-get install x11-dev
sudo apt-get install build-essential
sudo apt-get install checkinstall
sudo apt-get install cvs git-core mercurial
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install libumfpack
sudo apt-get install libumfpack4-dev
sudo apt-get install bootparamd
sudo apt-get install enamdict
sudo apt-get install libarpack2
sudo apt-get install libarpack2-dev
sudo apt-get install libarpack++2c2a
sudo apt-get install libarpack++2-dev
sudo apt-get install glpk
sudo apt-get install libglpk0
sudo apt-get install libncurses5-dev 
sudo apt-get install libreadline5-dev 
sudo apt-get install libsuitesparse-dev 
sudo apt-get install fftw3-dev 
sudo apt-get install libglpk-dev 
sudo apt-get install libhdf5-serial-dev 
sudo apt-get install libpcre3-dev 
sudo apt-get install libqhull-dev 
sudo apt-get install gperf 
sudo apt-get install gnuplot
==========================================

5) I installed "apt-file" and "autop-apt" to resolve dependencies ([https://help.ubuntu.com/community/CompilingEasyHowTo):](https://help.ubuntu.com/community/CompilingEasyHowTo):)

sudo dpkg --purge selinux-policy-default
sudo apt-get install apt-file

sudo apt-get install auto-apt
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local

6) I run first "configure" with "auto-apt" to check for and install missing libraries:

==========================================
sudo auto-apt run ./configure
==========================================

(I didn't install anything asking for "selinux-policy-default" because it gave me lots of problems)

7) I run again "configure" normally with some options:

==========================================
./configure --prefix=/usr/local/OCTAVE3p2 --srcdir=/usr/local/src/octave-3.2.0 --with-f77=gfortran --without-ccolamd --without-colamd --without-cxsparse --without-umfpack

[...]

Octave is now configured for i686-pc-linux-gnu

  Source directory:     .
  Installation prefix:  /usr/local/OCTAVE3p2
  C compiler:           gcc  -mieee-fp  -Wall -W -Wshadow -Wformat -g -O2
  C++ compiler:         g++  -mieee-fp -I/usr/include/freetype2  -Wall -W -Wshadow -Wold-style-cast -Wformat -g -O2
  Fortran compiler:     g77 -O -mieee-fp
  Fortran libraries:     -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../.. -L/lib/../lib -L/usr/lib/../lib -lhdf5 -lz -lfrtbegin -lg2c -lm
  BLAS libraries:       -llapack -lcblas -lf77blas -latlas
  FFTW libraries:       -lfftw3 -lfftw3f
  GLPK libraries:       -lglpk
  UMFPACK libraries:
  AMD libraries:        -lamd
  CAMD libraries:
  COLAMD libraries:
  CCOLAMD libraries:
  CHOLMOD libraries:
  CXSPARSE libraries:
  ARPACK libraries:     -larpack
  QRUPDATE libraries:
  HDF5 libraries:       -lhdf5
  CURL libraries:
  REGEX libraries:      -L/usr/lib -lpcre
  QHULL libraries:      -lqhull
  OPENGL libraries:     -lftgl -lfreetype -lz -L/usr/X11R6/lib -lGL -lGLU
  FLTK backend libs:    -lfltk_gl -lfltk
  X11 include flags:
  X11 libraries:        -L/usr/X11R6/lib -lX11
  CARBON libraries:
  LIBS:                 -lreadline  -lncurses -ldl -lcblas -lf77blas -latlas -lhdf5 -lz -lm
  Default pager:        less
  gnuplot:              gnuplot
  Magick config:

  Do internal array bounds checking:  false
  Build static libraries:             false
  Build shared libraries:             true
  Dynamic Linking:                    true (dlopen)
  Include support for GNU readline:   true
  64-bit array dims and indexing:     false

configure: WARNING: UMFPACK not found.  This will result in some lack of functionality for sparse matrices.
configure: WARNING: qrupdate not found. The QR & Cholesky updating functions will be slow.
configure: WARNING: COLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CCOLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CHOLMOD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CXSparse not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: GraphicsMagick++ config script not found.  Assuming GraphicsMagic++ library and header files are missing, so imread will not be fully functional
configure:

NOTE: libraries may be skipped if a library is not found OR
      if the library on your system is missing required features.
==========================================

8.) I compile the Makefile:

==========================================
make 

[...]

rm -f liboctinterp.so.3.2.0
ln -s liboctinterp.so liboctinterp.so.3.2.0
gcc -c  -I. -I.. -I../liboctave -I../src -I../libcruft/misc  -DHAVE_CONFIG_H -mieee-fp -Wall -W -Wshadow -Wformat -g -O2 main.c -o main.o
g++  -I. -I.. -I../liboctave -I../src -I../libcruft/misc  -DHAVE_CONFIG_H -mieee-fp -I/usr/include/freetype2 -Wall -W -Wshadow -Wold-style-cast -Wformat -g -O2 -rdynamic \
        -L..  -fPIC  -o octave \
        main.o  \
        -L../liboctave -L../libcruft -L../src -Wl,-rpath -Wl,/usr/local/OCTAVE3p2/lib/octave-3.2.0 \
        -loctinterp -loctave  -lcruft   \
          -lamd   \
           -llapack -lcblas -lf77blas -latlas \
        -lfftw3 -lfftw3f  -larpack -lftgl -lfreetype -lz -L/usr/X11R6/lib -lGL -lGLU \
        -L/usr/X11R6/lib -lX11  -lreadline  -lncurses -ldl -lcblas -lf77blas -latlas -lhdf5 -lz -lm  -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../.. -L/lib/../lib -L/usr/lib/../lib -lhdf5 -lz -lfrtbegin -lg2c -lm
g++ -c  -fPIC -I. -I.. -I../liboctave -I../src -I../libcruft/misc -DHAVE_CONFIG_H -mieee-fp -I/usr/include/freetype2 -Wall -W -Wshadow -Wold-style-cast -Wformat -g -O2 ./DLD-FUNCTIONS/amd.cc -o pic/amd.o
./DLD-FUNCTIONS/amd.cc: In function ‘octave_value_list Famd(const octave_value_list&, int)’:
./DLD-FUNCTIONS/amd.cc:174: error: ‘amd_malloc’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:175: error: ‘amd_free’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:176: error: ‘amd_calloc’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:177: error: ‘amd_realloc’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:178: error: ‘amd_printf’ was not declared in this scope
make[2]: *** [pic/amd.o] Error 1
make[2]: Leaving directory `/usr/local/src/octave-3.2.0/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/usr/local/src/octave-3.2.0'
make: *** [all] Error 2
==========================================

9) My questions are:

==========================================
a) Why I get this errors after doing "make"!!?

b) Why the problem seems related to "amd" libreries but "configure" does not tell me any warning or error with them?

c) Why the "configure" output is still using "g77" fortran compiler if in my options I told him to use "gfortran"? (see [http://www.centos.org/modules/newbb/viewtopic.php?topic_id=7958](http://www.centos.org/modules/newbb/viewtopic.php?topic_id=7958))

d) Why the "configure" output is warning me about UMFPACK, COLAMD, [...] libreries if in my options I told him to disable them? (as explained in INSTALL.OCTAVE file)

d) Why my directory "/usr/local/OCTAVE3p2" is absolutely empty!?
==========================================

Please help. I have spend too many hours with all this... I am about to giving up!!

Many thanks.

Ser.

---

### Post by serxyz on 2009-06-30
Sorted :mrgreen:

S.

==================================================================
$ ./configure --prefix=/usr/local/OCTAVE3p2 --srcdir=/usr/local/src/octave-3.2.0 --with-g77=gfortran --without-amd --without-ccolamd --without-colamd --without-cxsparse --without-umfpack

[...]

Octave is now configured for i686-pc-linux-gnu

  Source directory:     .
  Installation prefix:  /usr/local/OCTAVE3p2
  C compiler:           gcc  -mieee-fp  -Wall -W -Wshadow -Wformat -g -O2
  C++ compiler:         g++  -mieee-fp -I/usr/include/freetype2  -Wall -W -Wshadow -Wold-style-cast -Wformat -g -O2
  Fortran compiler:     g77 -O -mieee-fp
  Fortran libraries:     -L/usr/lib/gcc/i486-linux-gnu/3.4.6 -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/3.4.6/../../.. -L/lib/../lib -L/usr/lib/../lib -lhdf5 -lz -lfrtbegin -lg2c -lm
  BLAS libraries:       -llapack -lcblas -lf77blas -latlas
  FFTW libraries:       -lfftw3 -lfftw3f
  GLPK libraries:       -lglpk
  UMFPACK libraries:
  AMD libraries:
  CAMD libraries:
  COLAMD libraries:
  CCOLAMD libraries:
  CHOLMOD libraries:
  CXSPARSE libraries:
  ARPACK libraries:     -larpack
  QRUPDATE libraries:
  HDF5 libraries:       -lhdf5
  CURL libraries:
  REGEX libraries:      -L/usr/lib -lpcre
  QHULL libraries:      -lqhull
  OPENGL libraries:     -lftgl -lfreetype -lz -L/usr/X11R6/lib -lGL -lGLU
  FLTK backend libs:    -lfltk_gl -lfltk
  X11 include flags:
  X11 libraries:        -L/usr/X11R6/lib -lX11
  CARBON libraries:
  LIBS:                 -lreadline  -lncurses -ldl -lcblas -lf77blas -latlas -lhdf5 -lz -lm
  Default pager:        less
  gnuplot:              gnuplot
  Magick config:

  Do internal array bounds checking:  false
  Build static libraries:             false
  Build shared libraries:             true
  Dynamic Linking:                    true (dlopen)
  Include support for GNU readline:   true
  64-bit array dims and indexing:     false

configure: WARNING: UMFPACK not found.  This will result in some lack of functionality for sparse matrices.
configure: WARNING: qrupdate not found. The QR & Cholesky updating functions will be slow.
configure: WARNING: AMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: COLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CCOLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CHOLMOD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CXSparse not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: GraphicsMagick++ config script not found.  Assuming GraphicsMagic++ library and header files are missing, so imread will not be fully functional
configure:

NOTE: libraries may be skipped if a library is not found OR
      if the library on your system is missing required features.

==================================================================
$ make

[...]

Octave successfully built.  Now choose from the following:

   ./run-octave    - to run in place to test before installing
   make check      - to run the tests
   make install    - to install (PREFIX=/usr/local/OCTAVE3p2)

make[1]: Leaving directory `/usr/local/src/octave-3.2.0'
==================================================================
$ make check

make -f octMakefile check
make[1]: Entering directory `/usr/local/src/octave-3.2.0'
make -C test check
make[2]: Entering directory `/usr/local/src/octave-3.2.0/test'
./build_sparse_tests.sh
../run-octave --norc --silent --no-history ./fntests.m .

Integrated test scripts:

  src/DLD-FUNCTIONS/besselj.cc ........................... PASS  180/180
  src/DLD-FUNCTIONS/betainc.cc ........................... PASS    6/6
  src/DLD-FUNCTIONS/bsxfun.cc ............................ PASS   55/55
  src/DLD-FUNCTIONS/cellfun.cc ........................... PASS   74/74
  src/DLD-FUNCTIONS/chol.cc .............................. PASS   23/23
  src/DLD-FUNCTIONS/conv2.cc ............................. PASS    2/2
  src/DLD-FUNCTIONS/convhulln.cc ......................... PASS    2/2
  src/DLD-FUNCTIONS/dassl.cc ............................. PASS    4/4
  src/DLD-FUNCTIONS/det.cc ............................... PASS    5/5
  src/DLD-FUNCTIONS/dispatch.cc .......................... PASS    9/9
  src/DLD-FUNCTIONS/dlmread.cc ........................... PASS   20/20
  src/DLD-FUNCTIONS/dmperm.cc ............................ PASS    1/1
  src/DLD-FUNCTIONS/eig.cc ............................... PASS   20/20
  src/DLD-FUNCTIONS/eigs.cc ..............................A(I): Index exceeds matrix dimension.

make[2]: Leaving directory `/usr/local/src/octave-3.2.0/test'
make[1]: Leaving directory `/usr/local/src/octave-3.2.0'
==================================================================
$ sudo checkinstall

[...]

Done. The new package has been installed and saved to

/usr/local/src/octave-3.2.0/octave_3.2.0-1_i386.deb

You can remove it from your system anytime using:

     dpkg -r octave
==================================================================
/usr/local/OCTAVE3p2/bin/octave
==================================================================

---

### Post by nsnmb on 2009-11-16
Hi, [serxyz]("http://ubuntuforums.org/member.php?u=403754"),I run into a similiar problem as you did, fortunately you solved it already. I didn't yet.

I also plan to change from Matlab to Octave, and I installed many things:
1. f2c
2. fort77
3. Gnuplot

Then I started to install Octave, I download the Octave3.2.0 tar.gz, extra it with command: tar -xzf ...
Then, I compilie it with 
 ./configure
then, some warning came up, I ignored it and went to the next step with the command:
make
then error happens as followed:

make[2]: *** [octave] Error 1
make[2]: Leaving directory `/opt/Gnu_Octave/Install_file/octave-3.2.3/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/opt/Gnu_Octave/Install_file/octave-3.2.3'
make: *** [all] Error 2

I am afriad if you could give me a hand there? As you mentioned, I am about to giving up...

Thanks in advance...

---

### Post by jsampaio57 on 2009-12-15
use 
sudo apt-get build-dep octave3.2

Be careful because some graphical libraries may be uninstalled. After, assure you install the following libraries:

libumfpack
libcholmod
libcxsparse-dev
libqrupdate-dev
libcurl
libgraphicsMagick++1-dev

Cheers...
Jorge

---

### Post by jsampaio57 on 2009-12-15
oh... I skipped some libraries... include also

libamd
libcamd
libcolamd
libccolamd


if you are using 64-bit machine you can try using --enable-64 (but it is still experimental)

cheers...
Jorge

---

### Post by nsnmb on 2010-04-06
Hi jsampaio57, Thanks so much for your help.

I made a  new configure with command:
./configure F77=fort77 CPPFLAGS=-I/usr/include/freetype2 FLIBS=-lf2c

but error came up again with new hints like follows:
make[3]: *** [libcruft.so] Error 1
make[3]: Leaving directory `/opt/G_Octave/octave-3.2.3/libcruft'
make[2]: *** [libraries] Error 2
make[2]: Leaving directory `/opt/G_Octave/octave-3.2.3/libcruft'
make[1]: *** [libcruft] Error 2
make[1]: Leaving directory `/opt/G_Octave/octave-3.2.3'
make: *** [all] Error 2

I guess situation became better, but problem still there. Could you please a little bit check that? 

I shamed myself because of this stupid questiosn, sorry! 

Have a nice day!

---

