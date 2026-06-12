---
title: "netcdf-fortran configure error"
date: 2024-10-08
forum: Education &amp; Science
---

### Post by anelito76 on 2024-10-08
I try to install netcdf in UBUNTU 24.04.1 following:
 [https://www2.mmm.ucar.edu/wrf/OnLineTutorial/compilation_tutorial.php](https://www2.mmm.ucar.edu/wrf/OnLineTutorial/compilation_tutorial.php)

I type:
export DIR=$(pwd)
export CC=gcc
export CXX=g++
export FC=gfortran
export FCFLAGS=-m64
export F77=gfortran
export FFLAGS=-m64
export JASPERLIB=$DIR/grib2/lib
export JASPERINC=$DIR/grib2/include
export LDFLAGS=-L$DIR/grib2/lib
export CPPFLAGS=-I$DIR/grib2/include
echo "Rutas establecidas"

tar xzvf netcdf-c-4.7.2.tar.gz
cd netcdf-c-4.7.2
./configure --prefix=$DIR/netcdf --disable-dap --disable-netcdf-4 --disable-shared
make
make install
export PATH=$DIR/netcdf/bin:$PATH
export NETCDF=$DIR/netcdf
cd ..
echo "netcdf-c-4.7.2 instalado"

export LIBS="-lnetcdf -lz"
tar xzvf netcdf-fortran-4.5.2.tar.gz
cd netcdf-fortran-4.5.2
/configure --prefix=$DIR/netcdf --disable-dap --disable-netcdf-4 --disable-shared

and I got an error:
checking netcdf.h usability... no
checking netcdf.h presence... no
checking for netcdf.h... no
configure: error: netcdf.h could not be found. Please set CPPFLAGS.

What should I do?
How should I set CPPFLAGS?
Or should I try newer netcdf version?

thanks in advance,
A

---

