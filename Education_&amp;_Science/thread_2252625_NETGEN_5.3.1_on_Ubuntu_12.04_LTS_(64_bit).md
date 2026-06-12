---
title: "NETGEN 5.3.1 on Ubuntu 12.04 LTS (64 bit)"
date: 2014-11-13
forum: Education &amp; Science
---

### Post by vaina on 2014-11-13
Hi all,
I know that Netgen 4.9.13 is included in Ubuntu packages but I'd like to test the last version. *Togl1.7* and *Tix8.4.3*  should be already set. If I try to configure, compile and  install```
./configure --with-tcl=/usr/lib/tcl8.5/  --with-tk=/usr/lib/tk8.5/ --with-togl=/usr/lib/Togl1.7 --enable-occ  --with-occ=/usr/lib/
make
sudo make install
```I obtain an error message:```
make  all-recursive
make[1]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1'
Making all in libsrc
make[2]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc'
Making all in general
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/general'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/general'
Making all in gprim
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/gprim'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/gprim'
Making all in linalg
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/linalg'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/linalg'
Making all in include
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/include'
Making all in meshing
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/meshing'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/meshing'
Making all in interface
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/interface'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/interface'
Making all in csg
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/csg'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/csg'
Making all in geom2d
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/geom2d'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/geom2d'
Making all in occ
make[3]: Entering directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/occ'
/bin/bash ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H  -I. -I../..  -I../../libsrc/include  -DOCCGEOMETRY -I/usr/lib//inc  -I/usr/include/opencascade -D_OCC64 -DHAVE_IOSTREAM -DHAVE_LIMITS  -DHAVE_LIMITS_H -DHAVE_IOMANIP -I"/usr/include/tcl8.5"   -g -O2 -fopenmp  -MT Partition_Inter2d.lo -MD -MP -MF .deps/Partition_Inter2d.Tpo -c -o  Partition_Inter2d.lo Partition_Inter2d.cxx
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../..  -I../../libsrc/include -DOCCGEOMETRY -I/usr/lib//inc  -I/usr/include/opencascade -D_OCC64 -DHAVE_IOSTREAM -DHAVE_LIMITS  -DHAVE_LIMITS_H -DHAVE_IOMANIP -I/usr/include/tcl8.5 -g -O2 -fopenmp -MT  Partition_Inter2d.lo -MD -MP -MF .deps/Partition_Inter2d.Tpo -c  Partition_Inter2d.cxx  -fPIC -DPIC -o .libs/Partition_Inter2d.o
In file included from Partition_Inter2d.ixx:28:0,
                 from Partition_Inter2d.cxx:33:
Partition_Inter2d.jxx:31:30: fatal error: BRepAlgo_AsDes.hxx: No such file or directory
compilation terminated.
make[3]: *** [Partition_Inter2d.lo] Error 1
make[3]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc/occ'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1/libsrc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user-a5/Downloads/netgen-5.3.1'
make: *** [all] Error 2
```Can anyone help me to fix the installation procudure?
Thanks for your attention.

---

### Post by leycec-3 on 2015-04-11
I recently ran into similar issues myself. As a consequence, the official Netgen wiki now provides [exhaustive instructions]("https://sourceforge.net/p/netgen-mesher/wiki/Home/#cb9d") for manually configuring, compiling, and installing Netgen under Ubuntu. I won't summarize them here. (They're fairly... *exhaustive*.) I will say, however, that Netgen's OpenCascade (OCC) integration appears to be fundamentally broken under Ubuntu. **If you remove the "*-occ" options from your "./configure" line, "make" should now run without errors.**

That said, it *is* possible to proceed further in the compilation with OCC integration enabled before *another* fatal error erupts. For the sake of posterity (and developer debugging), here's how.

1. Install OpenCascade Community Edition (OCE), OpenMPI, and Togl development headers.
> sudo apt-get install liboce-foundation-dev liboce-modeling-dev liboce-ocaf-dev liboce-ocaf-lite-dev liboce-visualization-dev libopenmpi-dev libtogl-dev

2. Add OCE and OpenMPI include directories to the ${CPPFLAGS} variable.
>     CPPFLAGS="-I/usr/include/oce/ -I/usr/lib/openmpi/include/"
    export CPPFLAGS

3. Configure Netgen.
>     ./configure --with-sysroot=/usr/lib/ --with-tcl=/usr/lib/tcl8.5/ --with-tk=/usr/lib/tk8.5/ --with-togl=/usr/lib/ --with-metis=/usr/lib/x86_64-linux-gnu/ --with-occ=/usr/share/oce-0.15 --enable-nglib --enable-occ

4. Compile Netgen.
>     make

That gets past the fatal error you describe, only to subsequently fail as follows:

> 
    libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -I../../libsrc/include -DOCCGEOMETRY -I/usr/share/oce-0.15/inc -I/usr/include/opencascade -D_OCC64 -DHAVE_IOSTREAM -DHAVE_LIMITS -DHAVE_LIMITS_H -DHAVE_IOMANIP -I/usr/include/tcl8.5 -I/usr/include/oce/ -I/usr/lib/openmpi/include/ -g -O2 -fopenmp -DPARALLEL -MT Partition_Loop2d.lo -MD -MP -MF .deps/Partition_Loop2d.Tpo -c Partition_Loop2d.cxx  -fPIC -DPIC -o .libs/Partition_Loop2d.o
    Partition_Loop2d.cxx: In function 'Standard_Boolean SelectEdge(const BRepAdaptor_Surface&, const TopoDS_Edge&, const TopoDS_Vertex&, TopoDS_Edge&, const TopTools_ListOfShape&)':
    Partition_Loop2d.cxx:213:34: error: 'PI' was not declared in this scope
         Standard_Real anglemin = 3 * PI, tolAng = 1.e-8;
                                      ^
    Partition_Loop2d.cxx:237:30: error: 'tolAng' was not declared in this scope
           if (PI - Abs(angle) <= tolAng)
                                  ^
    Partition_Loop2d.cxx:254:63: error: 'tolAng' was not declared in this scope
           Standard_Boolean isClose = ( Abs( angle - anglemin ) <= tolAng );
                                                                   ^
    Makefile:427: recipe for target 'Partition_Loop2d.lo' failed
    make[3]: *** [Partition_Loop2d.lo] Error 1
    make[3]: Leaving directory '/home/pietakio/tmp/netgen-5.3.1/libsrc/occ'
    Makefile:311: recipe for target 'all-recursive' failed
    make[2]: *** [all-recursive] Error 1
    make[2]: Leaving directory '/home/pietakio/tmp/netgen-5.3.1/libsrc'
    Makefile:354: recipe for target 'all-recursive' failed
    make[1]: *** [all-recursive] Error 1
    make[1]: Leaving directory '/home/pietakio/tmp/netgen-5.3.1'
    Makefile:285: recipe for target 'all' failed
    make: *** [all] Error 2


My gut intuition is that Netgen's OCC integration is fundamentally broken. Hopefully, someone with substantially more time (and stoic willpower) can run with this from here.

---

