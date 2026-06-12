---
title: "netcdf4-python install"
date: 2011-06-29
forum: Education &amp; Science
---

### Post by RENOO on 2011-06-29
Hello,

I am trying to install [netcdf4-python]("http://code.google.com/p/netcdf4-python") on my kubuntu 11.04
Following the [wiki]("http://code.google.com/p/netcdf4-python/wiki/UbuntuInstall") , I have first installed the hdf5-1.8.7 package. I have first tried from the repo, then I did it from the source.
This step went well (I guess). It is quite a long compilation process.

I have installed everything in /opt in now contain /bin, /lib and /include directories
Now I am trying to install the netcdf-4.1.3 package.
I am using the following command

```
./configure --enable-netcdf-4 --with-hdf5=/opt/include/ --enable-share --prefix=/opt
```But I get the following error :

```
checking for floor in -lm... yes
checking for library containing H5Fflush... -lhdf5
checking for library containing H5DSis_scale... -lhdf5_hl
checking hdf5.h usability... no
checking hdf5.h presence... no
checking for hdf5.h... no
configure: error: NetCDF-4 requires HDF5, but hdf5.h cannot be found.

```What I don't understand is that hdf5.h is present in the include directory
```
/opt/netcdf-4.1.3$ ls -l /opt/include/hdf5*
-rw-r--r-- 1 root root 2655 2011-06-29 13:46 /opt/include/hdf5.h
-rw-r--r-- 1 root root 1553 2011-06-29 13:46 /opt/include/hdf5_hl.h


```Any help will be very much appreciate :)

---

### Post by javierarias on 2011-10-27
I had a similar issue, and I fix it changing the environment variables at compilation time.

Instead of 

./configure --enable-netcdf-4 --with-hdf5=/opt/hdf5/ --enable-share --prefix=/opt

You can try with:

CFLAGS="-I/opt/hdf5/current/include -L/opt/hdf5/current/lib" ./configure --enable-netcdf-4 --with-hdf5=/opt/hdf5/ --enable-share --prefix=/opt

With this change I manage to get rid of this:

checking hdf5.h usability... no
checking hdf5.h presence... no
checking for hdf5.h... no
configure: error: NetCDF-4 requires HDF5, but hdf5.h cannot be found.


It compiled fine, and it passed all the compilation tests.  :D

---

### Post by moldaviax on 2011-10-28
did you manage to get vcdat working?

M.

---

### Post by Karl Bas on 2012-01-23
Hi there!

I have a problem with installing netcdf4-python and hope someone could help me. 
I followed the instructions given here [http://code.google.com/p/netcdf4-python/wiki/UbuntuInstall](http://code.google.com/p/netcdf4-python/wiki/UbuntuInstall) , everything seems to work until step 3. There do not appear directories of hdf5 and netcdf4 in the desired usr/local directory, but libraries of hdf5 and netcdf4 in usr/local/lib and setup.py isn't there as well.
I run ubuntu 11.10, thanks in advance!

---

### Post by juanvi on 2012-03-08
I am in a similar situation as Karl Bas.
I am running ubuntu 11.10 and have followed the instructions [http://code.google.com/p/netcdf4-python/wiki/UbuntuInstall](http://code.google.com/p/netcdf4-python/wiki/UbuntuInstall). 
In order to install netcdf4-python I have downloaded: netCDF4-0.9.9.tar.gz from [http://code.google.com/p/netcdf4-python/downloads/detail?name=netCDF4-0.9.9.tar.gz&can=2&q=](http://code.google.com/p/netcdf4-python/downloads/detail?name=netCDF4-0.9.9.tar.gz&can=2&q=)
and have done: 
```
sudo python setup.py install
```
obtaining the following output:
```
HDF5_DIR environment variable not set, checking some standard locations ..
checking /home/jvcantavella ...
checking /usr/local ...
HDF5 found in /usr/local

NETCDF4_DIR environment variable not set, checking standard locations..
checking /home/jvcantavella ...
checking /usr/local ...
netCDF4 found in /usr/local
running install
running build
running config_cc
unifing config_cc, config, build_clib, build_ext, build commands --compiler options
running config_fc
unifing config_fc, config, build_clib, build_ext, build commands --fcompiler options
running build_src
build_src
building py_modules sources
building extension "netCDF4" sources
build_src: building npy-pkg config files
running build_py
running build_ext
customize UnixCCompiler
customize UnixCCompiler using build_ext
building 'netCDF4' extension
compiling C sources
C compiler: gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC

compile options: '-I/usr/local/include -I/usr/local/include -I/usr/lib/pymodules/python2.7/numpy/core/include -I/usr/include/python2.7 -c'
gcc: netCDF4.c
netCDF4.c: In function ‘__pyx_pf_7netCDF4_10_Dimension___init__’:
netCDF4.c:5762:13: warning: variable ‘__pyx_v_dim’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_7Dataset_2__exit__’:
netCDF4.c:14953:13: warning: variable ‘__pyx_v_traceback’ set but not used [-Wunused-but-set-variable]
netCDF4.c:14952:13: warning: variable ‘__pyx_v_value’ set but not used [-Wunused-but-set-variable]
netCDF4.c:14951:13: warning: variable ‘__pyx_v_atype’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_7Dataset_7_redef’:
netCDF4.c:15772:7: warning: variable ‘__pyx_v_ierr’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_7Dataset_8_enddef’:
netCDF4.c:15802:7: warning: variable ‘__pyx_v_ierr’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_8Variable___init__’:
netCDF4.c:21309:7: warning: implicit declaration of function ‘nc_get_var_chunk_cache’ [-Wimplicit-function-declaration]
netCDF4.c:21364:7: warning: implicit declaration of function ‘nc_set_var_chunk_cache’ [-Wimplicit-function-declaration]
netCDF4.c:21708:33: error: ‘NC_CONTIGUOUS’ undeclared (first use in this function)
netCDF4.c:21708:33: note: each undeclared identifier is reported only once for each function it appears in
netCDF4.c:21746:33: error: ‘NC_CHUNKED’ undeclared (first use in this function)
netCDF4.c:21880:117: warning: pointer targets in passing argument 4 of ‘nc_def_var_chunking’ differ in signedness [-Wpointer-sign]
/usr/local/include/netcdf.h:661:1: note: expected ‘int *’ but argument is of type ‘size_t *’
netCDF4.c: In function ‘__pyx_pf_7netCDF4_8Variable_11chunking’:
netCDF4.c:24815:109: warning: pointer targets in passing argument 4 of ‘nc_inq_var_chunking’ differ in signedness [-Wpointer-sign]
/usr/local/include/netcdf.h:665:1: note: expected ‘int *’ but argument is of type ‘size_t *’
netCDF4.c: In function ‘__pyx_pf_7netCDF4_10_Dimension___init__’:
netCDF4.c:5762:13: warning: variable ‘__pyx_v_dim’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_7Dataset_2__exit__’:
netCDF4.c:14953:13: warning: variable ‘__pyx_v_traceback’ set but not used [-Wunused-but-set-variable]
netCDF4.c:14952:13: warning: variable ‘__pyx_v_value’ set but not used [-Wunused-but-set-variable]
netCDF4.c:14951:13: warning: variable ‘__pyx_v_atype’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_7Dataset_7_redef’:
netCDF4.c:15772:7: warning: variable ‘__pyx_v_ierr’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_7Dataset_8_enddef’:
netCDF4.c:15802:7: warning: variable ‘__pyx_v_ierr’ set but not used [-Wunused-but-set-variable]
netCDF4.c: In function ‘__pyx_pf_7netCDF4_8Variable___init__’:
netCDF4.c:21309:7: warning: implicit declaration of function ‘nc_get_var_chunk_cache’ [-Wimplicit-function-declaration]
netCDF4.c:21364:7: warning: implicit declaration of function ‘nc_set_var_chunk_cache’ [-Wimplicit-function-declaration]
netCDF4.c:21708:33: error: ‘NC_CONTIGUOUS’ undeclared (first use in this function)
netCDF4.c:21708:33: note: each undeclared identifier is reported only once for each function it appears in
netCDF4.c:21746:33: error: ‘NC_CHUNKED’ undeclared (first use in this function)
netCDF4.c:21880:117: warning: pointer targets in passing argument 4 of ‘nc_def_var_chunking’ differ in signedness [-Wpointer-sign]
/usr/local/include/netcdf.h:661:1: note: expected ‘int *’ but argument is of type ‘size_t *’
netCDF4.c: In function ‘__pyx_pf_7netCDF4_8Variable_11chunking’:
netCDF4.c:24815:109: warning: pointer targets in passing argument 4 of ‘nc_inq_var_chunking’ differ in signedness [-Wpointer-sign]
/usr/local/include/netcdf.h:665:1: note: expected ‘int *’ but argument is of type ‘size_t *’
error: Command "gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/local/include -I/usr/local/include -I/usr/lib/pymodules/python2.7/numpy/core/include -I/usr/include/python2.7 -c netCDF4.c -o build/temp.linux-i686-2.7/netCDF4.o" failed with exit status 1
```

any idea?
Thank you in advance,

---

### Post by juanvi on 2012-03-08
Well, didn't succeed in installing netCDF4-0.9.9 but I did for netCDF4-0.9

---

### Post by lukegre@gmail.com on 2012-11-28
> **javierarias said:**
> I had a similar issue, and I fix it changing the environment variables at compilation time.

Instead of 

./configure --enable-netcdf-4 --with-hdf5=/opt/hdf5/ --enable-share --prefix=/opt

You can try with:

CFLAGS="-I/opt/hdf5/current/include -L/opt/hdf5/current/lib" ./configure --enable-netcdf-4 --with-hdf5=/opt/hdf5/ --enable-share --prefix=/opt

With this change I manage to get rid of this:

checking hdf5.h usability... no
checking hdf5.h presence... no
checking for hdf5.h... no
configure: error: NetCDF-4 requires HDF5, but hdf5.h cannot be found.


It compiled fine, and it passed all the compilation tests.  :D

Worked for me! Been struggling with this for a while. thanks a ton

---

