---
title: "Compiling Delft3D and mpich2"
date: 2012-04-27
forum: Education &amp; Science
---

### Post by cpgos on 2012-04-27
One of the prerequisites for a package that I want to use, Delft3D, is mpich2 but for everything to work correctly Delft3D and mpich2 both need to be compiled with the same compiler, in this case Intel Fortran Compiler v12.

The instructions in the readme file included with the MPICH2-1.4.1p1 release were followed and completed without error but compiling Delft3D fails, see attached file for mpich installation commands.

The readme file includes instructions on how to disable Fortran support but not on how to specify a particular Fortran compiler to use.

Please indicate how to compile mpich2 using Intel Fortran compiler v12 or suggest a possible source for this information.

Best regards

---

### Post by cpgos on 2012-05-03
This problem of how to compile mpich2 using Intel Fortran compiler v12 was solved via the the very responsive mpich2 mailing list along with the mpich2 installation guide.

The key command turned out to be :

/home/hmrc/Mpich2/mpich2-1.4.1p1/configure
--prefix=/home/hmrc/mpich2-install |& tee c.txt F77=ifort FC=ifort

cpgos

---

