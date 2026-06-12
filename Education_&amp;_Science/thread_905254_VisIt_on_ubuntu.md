---
title: "VisIt on ubuntu"
date: 2008-08-30
forum: Education &amp; Science
---

### Post by lordhaworth on 2008-08-30
Hey all

has anyone got VisIt working on ubuntu? I have downloaded and extracted the file you get from the website 

[https://wci.llnl.gov/codes/visit/](https://wci.llnl.gov/codes/visit/)

however I actually have no clue how to run it! I cannot see anything in the extracted file which allows me to start up VisIt

I downloaded the Linux - x86 32 bit
Redhat Enterprise Linux 4, ellipse.uchicago.edu 2.6.9-42.0.10.ELsmp, icc 9.1 & gcc 3.4.6

from

[https://wci.llnl.gov/codes/visit/executables.html](https://wci.llnl.gov/codes/visit/executables.html)

and everything extracted fine its just a case of how do I start it?!??!?!?!


Cheers 

Tom

---

### Post by Sef on 2008-08-30
ubuntu uses .deb, while Redhat uses .rpm.  You need some software called Alien to convert .rpm to .deb.

For more information, read [psychocats installing software]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by lordhaworth on 2008-08-31
Thanks!

---

### Post by lordhaworth on 2008-09-06
Hey again, still having a spot of trouble with this...
The thing I am trying to launch is "visit" located at:

~/Applications/visit/bin$ ls
curv3dprep        silex            visitconvert      xml2java         xmledit
frontendlauncher  surfcomp         visit_plugin      xml2makefile     xmltest
legacylauncher    text2polys       visit_transition  xml2plugin
makemili          time_annotation  xml2atts          xml2projectfile
mkgrdbl           **visit**     xml2avt           xml2python
mpeg2encode       visit_composite  xml2info          xml2window

I have tried launching this in various ways...


```

$ ./visit (or $ sudo./visit)
Running: gui1.9.1
/home/lordhaworth/Applications/visit/1.9.1/linux-intel/bin/gui: error while loading shared libraries: libimf.so: cannot open shared object file: No such file or directory

```


```

$ alien visit
Must run as root to convert to deb format (or you may use fakeroot).

```


```

$ sudo alien visit  (or sudo alien ./visit)
Unknown type of package, visit.

```

Am I just using alien incorrectly?

Tom

---

### Post by @&amp;%$°¬ on 2008-09-08
Hi, I have some of your problems too. I just discovered VisIt today, and yes, there is only a compiled Linux version for RedHat or similar, but these don't come in a .rpm format nor .deb. You are not using alien incorrectly, the problem is that alien works on a .rpm file to generate a .deb (that Ubuntu can manage). But VisIt comes in a .tar.gz file format, that's why you need a script.

So, in order to install the .tar.gz file, you have to copy this script file:

[https://wci.llnl.gov/codes/visit/1.10.0/visit-install](https://wci.llnl.gov/codes/visit/1.10.0/visit-install)

and execute it as explained here:

[https://wci.llnl.gov/codes/visit/1.10.0/INSTALL_NOTES](https://wci.llnl.gov/codes/visit/1.10.0/INSTALL_NOTES)

This is so far where I could go. After this, a menu appears and I have tried every option without any success. I hope that may be these steps shine a light on somebody...

Andrés

---

### Post by lordhaworth on 2008-09-09
Thanks, well at least its one step closer!

---

### Post by EdSantilli on 2009-06-03
I have Visit 1.11.2 working on 32-bit Ubuntu 9.04.  Here's how I did it...

   1.) From [https://wci.llnl.gov/codes/visit/executables.html](https://wci.llnl.gov/codes/visit/executables.html) download two things: the install script and the Linux-x86 32 bit Redhat 3 tarball. (If you have a 64-bit system let me know...I will be installing Visit on a 64-bit system soon.)

   2.) Put both of these files in the SAME directory.  Open a terminal and goto that directory.

   3.) Type:  'sudo ./visit-install 1.11.2 linux_rhel3 /usr/local/visit' and press enter.  I answered 'No' for all of the questions.  Now just wait a few minutes for the script to run.

   4.) Now, Visit should be installed.  Goto the /usr/local/visit/bin directory.  Run ./legacylauncher to test if everything worked well.  If you get an error about libstdc++.so.5, just goto Synaptic and download libstdc++ 5.  Everything should work now.

---

### Post by lordhaworth on 2009-06-09
Heya, 

since the previous post I had got visit to the state that I could use it! It isn't perfect though so I might look in to your method and see if it resolves any of the minor issues

cheers

---

### Post by juxtaposicion on 2009-07-16
Hi, I tried this, installed it without sudo to a directory that I have full access to, but when I try running:

./visit/bin/visit -> Version 1.11.2 of 'gui' does not exist for 
the architecture 'linux-x86_64'.

and

./visit/bin/legacylauncher  -> No versions of VisIt have been installed for this hardware platform.

...although the install seems to do just fine. What's going on? Do I need sudo?

chris

---

### Post by lordhaworth on 2009-07-20
I got that same error after trying visit after I did a fresh install of ubuntu

Mine works now, I'll check in my lab book exactly what I did - but off the top of my head I think you need to do a 

set LD_LIBRARY_PATH 


to somewhere I cant remember atm - ill post the fix tonight if I remember

---

### Post by lordhaworth on 2009-07-20
oh yeah, and in response to my original question - you do just got into ./visit/bin/visit

---

### Post by lordhaworth on 2009-07-21
I had to use

setenv LD_LIBRARY_PATH /usr/lib

before it would work without the message you were getting juxtaposicion.

type that into the terminal and try again, note that you will nedd tcsh or csh for it to work.

if you start in bash shell - type:

```

tcsh

``` 

and download it if necessary, then type:

```

setenv LD_LIBRARY_PATH /usr/lib/

```
 

and try running it as you were before

---

### Post by juxtaposicion on 2009-07-28
Hi, is there anything else you did? I still get the same error message after modifying the LD_LIBRARY_PATH variable to include /usr/lib. 

I've in addition tried setting the LD_LIBRARY_PATH variable in bash as well, to no avail.

Thanks!
chris

---

### Post by valval on 2009-08-05
I installed VisIt from source successfully on my Ubuntu 9.04. It is version 1.11.2 with HDF5 support. See the steps below. 

Best regards,
valval


```
#-----------------------------------------------
# Instructions for building VisIt 1.11.2
# on Ubuntu 9.04
#-----------------------------------------------

#-----------------------------------------------
# Prep
#-----------------------------------------------

# Some .deb packages that are likely necessary for the build:
sudo apt-get install build-essential
sudo apt-get install m4
sudo apt-get install gfortran
sudo apt-get install fortran77-compiler

# Get your environment ready:
mkdir visit-build
cd visit-build
mkdir visit
setenv VISITDIR `pwd`/visit
setenv VISITARCH ubuntu-9.04
setenv OBJECT_MODE 32
alias gmake make


#-----------------------------------------------
# Download
#-----------------------------------------------

wget [https://wci.llnl.gov/codes/visit/3rd_party/Mesa-5.0-mangled.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/Mesa-5.0-mangled.tar.gz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/cmake-2.4.5.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/cmake-2.4.5.tar.gz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/vtk-5.0.0c.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/vtk-5.0.0c.tar.gz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/qt-x11-free-3.3.8.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/qt-x11-free-3.3.8.tar.gz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/silo-4.6.2.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/silo-4.6.2.tar.gz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/Python-2.5.tgz](https://wci.llnl.gov/codes/visit/3rd_party/Python-2.5.tgz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/hdf5-1.6.5.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/hdf5-1.6.5.tar.gz)
wget [https://wci.llnl.gov/codes/visit/3rd_party/boxlib.tar.gz](https://wci.llnl.gov/codes/visit/3rd_party/boxlib.tar.gz)
wget [https://wci.llnl.gov/codes/visit/1.11.2/visit1.11.2.tar.gz](https://wci.llnl.gov/codes/visit/1.11.2/visit1.11.2.tar.gz)


#-----------------------------------------------
# Mesa
#-----------------------------------------------

tar xzf Mesa-5.0-mangled.tar.gz
cd Mesa-5.0
make linux
mkdir $VISITDIR/mesa
mkdir $VISITDIR/mesa/5.0
mkdir $VISITDIR/mesa/5.0/$VISITARCH
mkdir $VISITDIR/mesa/5.0/$VISITARCH/{include,lib}
mkdir $VISITDIR/mesa/5.0/$VISITARCH/include/GL
cp include/GL/*.h $VISITDIR/mesa/5.0/$VISITARCH/include/GL
cp lib/*.so       $VISITDIR/mesa/5.0/$VISITARCH/lib 
cd ..


#-----------------------------------------------
# cmake
#-----------------------------------------------

tar xzf cmake-2.4.5.tar.gz
cd cmake-2.4.5
env CXXFLAGS=""  CFLAGS="" ./bootstrap
gmake
cd ..


#-----------------------------------------------
# VTK
#-----------------------------------------------

tar xzf vtk-5.0.0c.tar.gz
cd VTK
../cmake-2.4.5/bin/cmake .

# Edit CMakeCache.txt:
#   BUILD_SHARED_LIBS:BOOL=ON
#   BUILD_TESTING:BOOL=OFF
#   VTK_USE_MANGLED_MESA:BOOL=ON

../cmake-2.4.5/bin/cmake .

# Edit CMakeCache.txt, setting MANGLED_MESA_INCLUDE_DIR, MANGLED_MESA_LIBRARY,
# MANGLED_OSMESA_INCLUDE_DIR, MANGLED_OSMESA_LIBRARY, to point to the
# appropriate files and directories in the mesa directory.
# For example:
#
# MANGLED_MESA_INCLUDE_DIR:PATH=$VISITDIR/mesa/5.0/$VISITARCH/include
# MANGLED_MESA_LIBRARY:FILEPATH=$VISITDIR/mesa/5.0/$VISITARCH/lib/libMesaGL.so
# MANGLED_OSMESA_INCLUDE_DIR:PATH=$VISITDIR/mesa/5.0/$VISITARCH/include
# MANGLED_OSMESA_LIBRARY:FILEPATH=$VISITDIR/mesa/5.0/$VISITARCH/lib/libOSMesa.so
#
# Note that you need to be very careful in setting the above variables so
# that you provide the appropriate filename or path.
#

../cmake-2.4.5/bin/cmake .
gmake

# Getting error: ‘memcpy’ was not declared in this scope
# on three files:
#   Utilities/DICOMParser/DICOMAppHelper.cxx
#   Utilities/DICOMParser/DICOMFile.cxx
#   Utilities/DICOMParser/DICOMParser.cxx
# This is likely due to using 4.3.3 g++ compiler.
# Edit the files and add to each:
#   #include <string.h>

gmake

mkdir $VISITDIR/vtk
mkdir $VISITDIR/vtk/5.0.0c
mkdir $VISITDIR/vtk/5.0.0c/$VISITARCH
mkdir $VISITDIR/vtk/5.0.0c/$VISITARCH/{Common,Filtering,GenericFiltering,Graphics,Hybrid,IO,Imaging,MangleMesaInclude,Rendering,Utilities,VolumeRendering,lib,vtkstd,Utilities/vtktiff,Utilities/vtkexpat,Utilities/vtkzlib}
cp vtkConfigure.h                   $VISITDIR/vtk/5.0.0c/$VISITARCH
cp vtkToolkits.h                    $VISITDIR/vtk/5.0.0c/$VISITARCH
cp vtk*Instantiator.h               $VISITDIR/vtk/5.0.0c/$VISITARCH
cp Common/*.h                       $VISITDIR/vtk/5.0.0c/$VISITARCH/Common
cp Common/*.txx                     $VISITDIR/vtk/5.0.0c/$VISITARCH/Common
cp Filtering/*.h                    $VISITDIR/vtk/5.0.0c/$VISITARCH/Filtering
cp Filtering/*.txx                  $VISITDIR/vtk/5.0.0c/$VISITARCH/Filtering
cp GenericFiltering/*.h             $VISITDIR/vtk/5.0.0c/$VISITARCH/GenericFiltering
cp Graphics/*.h                     $VISITDIR/vtk/5.0.0c/$VISITARCH/Graphics
cp Hybrid/*.h                       $VISITDIR/vtk/5.0.0c/$VISITARCH/Hybrid
cp IO/*.h                           $VISITDIR/vtk/5.0.0c/$VISITARCH/IO
cp Imaging/*.h                      $VISITDIR/vtk/5.0.0c/$VISITARCH/Imaging
cp Rendering/*.h                    $VISITDIR/vtk/5.0.0c/$VISITARCH/Rendering
cp Utilities/*.h                    $VISITDIR/vtk/5.0.0c/$VISITARCH/Utilities
cp Utilities/vtktiff/*.h            $VISITDIR/vtk/5.0.0c/$VISITARCH/Utilities/vtktiff
cp Utilities/vtkexpat/*.h           $VISITDIR/vtk/5.0.0c/$VISITARCH/Utilities/vtkexpat
cp Utilities/vtkzlib/*.h            $VISITDIR/vtk/5.0.0c/$VISITARCH/Utilities/vtkzlib
cp VolumeRendering/*.h              $VISITDIR/vtk/5.0.0c/$VISITARCH/VolumeRendering
cp MangleMesaInclude/*.h            $VISITDIR/vtk/5.0.0c/$VISITARCH/MangleMesaInclude
cp vtkstd/*                         $VISITDIR/vtk/5.0.0c/$VISITARCH/vtkstd
cp -d bin/*.so*                     $VISITDIR/vtk/5.0.0c/$VISITARCH/lib
cd ..


#-----------------------------------------------
# Qt
# NOTE: 3.3.2 did not work (could not make sub-src),
#       so using 3.3.8
#-----------------------------------------------

tar xzf qt-x11-free-3.3.8.tar.gz
cd qt-x11-free-3.3.8
setenv QTDIR `pwd`
set path=($QTDIR/bin $path)

setenv LD_LIBRARY_PATH $QTDIR/lib:$LD_LIBRARY_PATH
# NOTE: if LD_LIBRARY_PATH is not set in your environment, this command will
# fail.  In this case, just issue:
# setenv LD_LIBRARY_PATH $QTDIR/lib

./configure -platform linux-g++ -shared -qt-libpng
make symlinks
make src-qmake
make src-moc 
make sub-src

cd tools/designer/uilib
make

# Getting error:
#   make: *** [../../../lib/libqui.so.1.0.0] Error 1
# So, let's just make the whole thing.

cd ../../..
make

mkdir $VISITDIR/qt
mkdir $VISITDIR/qt/3.3.8
mkdir $VISITDIR/qt/3.3.8/$VISITARCH
mkdir $VISITDIR/qt/3.3.8/$VISITARCH/{bin,include,lib}
mkdir $VISITDIR/qt/3.3.8/$VISITARCH/include/private
cp bin/{findtr,moc,qt20fix,qtrename140} $VISITDIR/qt/3.3.8/$VISITARCH/bin
cd include; cp *.h $VISITDIR/qt/3.3.8/$VISITARCH/include
cp private/*.h $VISITDIR/qt/3.3.8/$VISITARCH/include/private
cd ../lib;find . -print | cpio -pvmud $VISITDIR/qt/3.3.8/$VISITARCH/lib
cd ../..


#-----------------------------------------------
# HDF5
#-----------------------------------------------

tar xzf hdf5-1.6.5.tar.gz
cd hdf5-1.6.5
./configure --disable-shared -prefix=$VISITDIR/hdf5/1.6.5/$VISITARCH
make

# Getting error:
#   call to '__open_missing_mode' declared with attribute 
#   error: open with O_CREAT in second argument needs 3 arguments
# Fix by editing file "perform/zip_perf.c" and changing line 548 to:
#           output = open(filename, O_RDWR | O_CREAT, S_IRWXU);
# See:
#   [http://hdf.ncsa.uiuc.edu/HDF5/release/known_problems5182.html](http://hdf.ncsa.uiuc.edu/HDF5/release/known_problems5182.html)

make

mkdir $VISITDIR/hdf5
mkdir $VISITDIR/hdf5/1.6.5
mkdir $VISITDIR/hdf5/1.6.5/$VISITARCH
make install
cd ..


#-----------------------------------------------
# Silo
#-----------------------------------------------

tar xzf silo-4.6.2.tar.gz
cd silo-4.6.2
env CFLAGS=-O2 ./configure --without-readline -with-hdf5=$VISITDIR/hdf5/1.6.5/$VISITARCH/include,$VISITDIR/hdf5/1.6.5/$VISITARCH/lib --without-exodus --prefix=$VISITDIR/silo/4.6.2/$VISITARCH
make 
make install
cd ..

# Silo is built dependent on HDF5, and Visit configure script
# looks for the dependent library in Silo's installation.
# Therefore, create a link there to the HDF5 library.
cd $VISITDIR/silo/4.6.2/$VISITARCH/lib
ln -s ../../../../hdf5/1.6.5/ubuntu-9.04/lib/libhdf5.a
cd $VISITDIR
cd ..

#sh silo060605.sh
#cd silo060605
#env CFLAGS=-O2 ./configure --without-readline --without-hdf5 --without-exodus
#make
#mkdir $VISITDIR/silo
#mkdir $VISITDIR/silo/4.5.1
#mkdir $VISITDIR/silo/4.5.1/$VISITARCH
#mkdir $VISITDIR/silo/4.5.1/$VISITARCH/{include,lib}
#cp silo/silo/silo.{h,inc}   $VISITDIR/silo/4.5.1/$VISITARCH/include
#cp silo/sdx/sdx.{h,inc}     $VISITDIR/silo/4.5.1/$VISITARCH/include
#cp lib/libsilo.a            $VISITDIR/silo/4.5.1/$VISITARCH/lib
#cd ..


#-----------------------------------------------
# Python
#-----------------------------------------------

tar xzf Python-2.5.tgz
cd Python-2.5
./configure --prefix=$VISITDIR/python/2.5/$VISITARCH
make
make install
mkdir tmpdir
cd tmpdir
ar -x ../libpython2.5.a
g++ -shared -o ../libpython2.5.so *.o                         
cd ..
rm -rf tmpdir
cp libpython2.5.so $VISITDIR/python/2.5/$VISITARCH/lib/python2.5/config/libpython2.5.so
cd ..


#-----------------------------------------------
# Boxlib
#-----------------------------------------------

tar xzf boxlib.tar.gz
cd CCSEApps/BoxLib

# Edit file ../mk/Make.Linux and comment out the two lines 
# that contain "-ffortran-bounds-check".

# Edit file GNUmakefile and change the USE_MPI flag:
#   USE_MPI   = FALSE
# Also change the compiler:
#   COMP      = g++

gmake -f GNUmakefile

# Getting error:
#   error: ‘abort’ was not declared in this scope
# Edit file "ParallelDescriptor.cpp" and add:
#   #include <cstdlib>

# Getting errors:
#   ../BoxLib/std/limits:26:24: error: stl_config.h: No such file or directory
# So, per VisIt BUILD_NOTES, move std:

mv std std.old
gmake -f GNUmakefile

mkdir $VISITDIR/boxlib
mkdir $VISITDIR/boxlib/$VISITARCH
mkdir $VISITDIR/boxlib/$VISITARCH/{include,lib}
mkdir $VISITDIR/boxlib/$VISITARCH/include/{2D,3D}
cp libbox3d*.a $VISITDIR/boxlib/$VISITARCH/lib/libbox3D.a
tar cf Boxlib3D.h.tar *.H
gmake clean

# Edit file GNUmakefile and change line "DIM = 3" to "DIM = 2".

gmake -f GNUmakefile

# Getting error:
#   BLThread.cpp:70: error: ‘strerror’ is not a member of ‘std’
# Edit file "BLThread.cpp" and add:
#   #include <cstring>

gmake -f GNUmakefile

# Getting error:
#   make: g77: Command not found
# Edit file ../mk/Make.Linux and change line:
#   FC       := g77 -fno-second-underscore          
# to the following:
#   FC       := f77 -fno-second-underscore

gmake -f GNUmakefile

cp libbox2d*.a $VISITDIR/boxlib/$VISITARCH/lib/libbox2D.a
tar cf Boxlib2D.h.tar *.H
cp Boxlib2D.h.tar $VISITDIR/boxlib/$VISITARCH/include/2D
cp Boxlib3D.h.tar $VISITDIR/boxlib/$VISITARCH/include/3D
cd $VISITDIR/boxlib/$VISITARCH/include/2D
tar xf Boxlib2D.h.tar
cd $VISITDIR/boxlib/$VISITARCH/include/3D
tar xf Boxlib3D.h.tar
cd $VISITDIR
cd ..


#-----------------------------------------------
# VisIt
#-----------------------------------------------

tar xzf visit1.11.2.tar.gz
cd visit1.11.2/src/config-site
echo VISITHOME=$VISITDIR > `hostname`.conf
sed "s/ARCH/$VISITARCH/" Template.conf >> `hostname`.conf
cd ..

# Edit file config-site/<hostname>.conf and change the following:
#
# We are using Qt version 3.3.8, so change the QT lines:
#   QT_BIN=$VISITHOME/qt/3.3.8/ubuntu-9.04/bin
#   QT_INCLUDE=$VISITHOME/qt/3.3.8/ubuntu-9.04/include
#   QT_LIB=$VISITHOME/qt/3.3.8/ubuntu-9.04/lib
#
# Also uncomment lines:
#   DEFAULT_BOXLIB*
#   DEFAULT_HDF5*
#
# We installed silo 4.6.2 so change the SILO line:
#   DEFAULT_SILO_LIBLOC=$VISITHOME/silo/4.6.2/ubuntu-9.04   

env LDFLAGS=-L$VISITDIR/python/2.5/ubuntu-9.04/lib/python2.5/config CPPFLAGS=-I$VISITDIR/python/2.5/ubuntu-9.04/include/python2.5 CFLAGS=-O2 CXXFLAGS=-O2 ./configure --with-silo=$VISITDIR/silo/4.6.2/ubuntu-9.04/include,$VISITDIR/silo/4.6.2/ubuntu-9.04/lib:-lhdf5 --with-hdf5=$VISITDIR/hdf5/1.6.5/ubuntu-9.04/include,$VISITDIR/hdf5/1.6.5/ubuntu-9.04/lib

make

# Getting errors build ddcMD database plugin.
# Edit file databases/Makefile and delete DDCMD from REQUIRED.

make

./svn_bin/visit-bin-dist
svn_bin/visit-install 1.11.2 linux $VISITDIR
```

---

### Post by ganesh_ae on 2009-08-09
1.Install tcsh
2.Download two files(visit-install,*.tar.gz) and put it in same folder
3.Open terminal and navigate into the folder.Type the following command
 
 visit-install 1.11.2 linux-x86_64 /usr/local/visit

4.say No to all.(two times)
Installation is over.

Set the path by adding following lines to the /etc/bash.bashrc file

#visit
PATH=/usr/local/visit/bin:PATH
export PATH

5.Type visit to run visit gui

Imp:If you are getting command not found error,run tcsh command and proceed

Note:
No need to run tcsh everytime
Dont use ./ or sh to run the commands or visit


Thanks to all.:)

---

### Post by padeco on 2009-10-31
hi guys,
do you have any other link that i may have a look. i have followed all the instructions, but the visit-install script is not working.

i get this error:
programs$ visit-install visit1_12_0.linux-x86_64-ubuntu8.tar.gz /home/local/programs/visit/
bash: visit-install: command not found

when i tried with sudo, still the same error. do i have to do anything to the "visit-install" first?
when i tried:

programs$ sudo sh build_visit visit1_12_0.linux-x86_64-ubuntu8.tar.gz /home/local/programs/visit/
build_visit: 789: [[: not found
build_visit: 789: [[: not found
build_visit: 789: [[: not found
build_visit: 789: [[: not found
build_visit: 789: [[: not found
build_visit: 789: [[: not found
build_visit: 789: [[: not found
build_visit: 809: [[: not found
build_visit: 922: [[: not found
build_visit: 929: [[: not found
build_visit: 949: [[: not found
build_visit: 969: [[: not found
build_visit: 1092: function: not found
build_visit: 1107: function: not found
build_visit: 1119: [[: not found
visit1_12_0.linux-x86_64-ubuntu8.tar.gz /home/local/programs/visit/
build_visit: 1119: [[: not found
build_visit: 1131: function: not found
build_visit: 1138: warn: not found
build_visit: 1138: warn: not found


any help would be much appreciated. i followed the advice in [https://wci.llnl.gov/codes/visit/1.10.0/INSTALL_NOTES](https://wci.llnl.gov/codes/visit/1.10.0/INSTALL_NOTES) and still no luck.

cheers,
padeco

---

### Post by teonghan on 2009-11-02
Hi all,

I have been using VisIt for quite some time for my final year project and master project. On Jaunty, you will just need to download the latest version of VisIt, normally the first link of "Linux - x86 32 bit" a.k.a [COLOR="Navy"][https://wci.llnl.gov/codes/visit/1.12.0/visit1_12_0.linux_rhel3.tar.gz]("https://wci.llnl.gov/codes/visit/1.12.0/visit1_12_0.linux_rhel3.tar.gz")[/COLOR]. Save it somewhere and extract it. Install libstdc++5 from your Synaptics/Apt. Go to the extracted visit folder, cd to bin folder and type ./visit in terminal. Voila!

For Karmic, libstdc++5 is not available on the repo. I went to [COLOR="Navy"][http://packages.debian.org/stable/base/libstdc++5]("http://packages.debian.org/stable/base/libstdc++5")[/COLOR] to get the libstdc++5 package and install it. After that VisIt can be run as usual.

Update:
For me, sometimes, after I have done the steps above, VisIt hangs when loading midway. I installed libreadline4 from [http://packages.ubuntu.com/dapper/i386/libreadline4/download]("http://packages.ubuntu.com/dapper/i386/libreadline4/download") and now my VisIt is Ok.

---

### Post by sportscliche on 2011-02-17
The install of VisIt on Ubuntu seems to have gotten easier since this discussion.  I got LLNL's RHEL4 binary script running on Ubuntu 10.04 following the instructions on their download page.  A few things aren't immediately obvious, so I'll describe the procedure I used in detail.

Make a folder in your home directory and call it anything you wish.  I named mine Visit. From the LLNL website

[https://wci.llnl.gov/codes/visit/executables.html](https://wci.llnl.gov/codes/visit/executables.html)

download visit2_2_0.linux-rhel4.tar.gz into this directory.  Do not unbundle!

Right-click and download visit-install2_2_0 from the link on the same LLNL page into the same directory.  Next

$chmod 755 visit-install2_2_0
$sudo ./visit-install2_2_0 2.2.0 linux-rhel4 /usr/local/visit

This launches the script that installs visit automatically.  I may have been lucky enough to have all the dependencies already installed because I did not get any error messages.  Verify it is operational from the command line with:

$/usr/local/visit/bin/visit

which brings up the visit GUI.  I did not do this as root.  Next you'll want to put visit in the user path.  Since the default shell in ubuntu is bash (not csh as shown in the LLNL instructions) edit .bashrc in your home directory with your favorite editor.  I added the following lines to the end of the .bashrc file:

#Add the visualization program visit to the search path
PATH=$PATH:/usr/local/visit/bin
export PATH

To enable, you can do a logout-login sequence or simply run
$source ~/.bashrc
$set

To make sure this worked, check

$echo $PATH

Now you should be able to launch visit without specifying a path

$visit

If so inclined, you can add it to your menu list using the procedure appropriate for your desktop environment.

---

