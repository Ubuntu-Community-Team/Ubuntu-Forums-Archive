---
title: "ROOT. how to install on ubuntu?"
date: 2007-06-11
forum: Education &amp; Science
---

### Post by dougleduck on 2007-06-11
Anyone out there know if any of the binary files for the ROOT particle physics tool can be easily installed?

If not how difficult is it the install from source given that I´m very new to linux. I´ve tried looking at the user guide on [http://root.cern.ch/](http://root.cern.ch/) but I´m lost.

---

### Post by meatpan on 2007-06-11
It looks like this package is in the debian 'experimental' repository:
[http://packages.debian.org/experimental/science/root-system](http://packages.debian.org/experimental/science/root-system)

Beware of experimental packages.  Here is debian's warning:
> 
Warning: This package is from the experimental distribution. That means it is likely unstable or buggy, and it may even cause data loss. If you ignore this warning and install it nevertheless, you do it on your own risk.


---

### Post by dougleduck on 2007-06-11
is this because its the ´new´version 5.15 or ROOT and not the stable´production´ version  5.14?

for whatever reason the stable 5.14 doesn appear to be around.

Would it be stable if i compiled 5.15 myself?

---

### Post by meatpan on 2007-06-11
Good question.  I'm really not sure why the software is in the experimental archive.  I took a closer look at the rationale for debian experimental packages (  [http://www.debian.org/doc/developers-reference/ch-resources](http://www.debian.org/doc/developers-reference/ch-resources) ) but couldn't find a set of specific criteria on a package-by-package basis.

---

### Post by lad.kocb on 2007-06-14
Anyone out there know if any of the binary files for the ROOT particle physics tool can be easily installed?
If not how difficult is it the install from source given that I´m very new to linux. I´ve tried looking at the user guide on [http://root.cern.ch/](http://root.cern.ch/) but I´m lost
--------------------------------------------------
I recommend own build. It is not that difficult

ROOT is not a fancy toy. It is (among other things) used as a production
tool in data analysis in some of the most demanding scientific projects.

Therefore the system is necessarily very conservative. For many purposes
(actually most)
you can exchange pieces of code between versions 2.x and 5.x.

Therefore you do not need the latest version.
get the source e.g. from a little bit "older" (about 6 months)
       [http://root.cern.ch/root/Version512.html](http://root.cern.ch/root/Version512.html)
and do not read the stuff there. It is for CERN people only.

I have just done an  "installation" from the mentioned "source tree"
unpacking the source:
- move the package  root-xxxxxx.tar.gz  from the desktop somewhere
IN THE TERMINAL:
- gunzip root-xxxxxx.tar.gz
- tar -xf root-xxxxxx.tar
- Now you can start  (the tar produced a new directory root  )
        cd root
       ./configure
- most probably at this stage it will refuse collaborate
  requiring various libraries and g77
- Using synaptic package manager try to get the packages
  in my case I needed  X11-devel (Scientific Linux notation, the script told me)
  on debian/ubuntu such packages are usually called dev  , not  devel
  in synaptic I searched x11  dev  and got a lot. I installed some x11proto-dev-base
  did not help much;  ./configure still refused
  after installing  xlibs-dev 
  and using     ./configure linuxdeb
  configure made the configuration (about 30 seconds)
             You might enter   ./configure --help      for info
- now we are prepared: simply type

    make

- make used 30 minutes on my notebook (ancient one)
  and finished then smoothly. It is interesting to watch it now and then
  to see what all is happening. Here some fortran, some moving, some g++
  som gcc  - but 30 minutes might be too long to watch. Read some news ....
  After the SUCCESS:

- instead of   make install 
- I said
     cd ..
  sudo mv root /usr/local
    Here I was asked for password
Then I have constructed the command "root" as a file
    /usr/bin/root
        #!/bin/bash
        export ROOTSYS=/usr/local/root
        $ROOTSYS/bin/root  $1 $2 $3 $4

I also naturally said
    chmod a+rx /usr/bin/root

So now I have a fresh installation of root  - thanks to your question!

You can do no harm to your linux installation, since root
keeps everything under one directory. If it does not work, you simply
remove all the "root" from where you installed it.
(CAREFULL!  do not remove /root   -- that is a different file )

ROOT should be used by many, it is nearly as useful as octave, and it is
by no means limited to particle physics.

Normally, you would run root in a terminal window

I also recommend:
     cd /usr/local/root
    cp -r  tutorials   ~/ROOTwork

Then test it all by
     cd  ~/ROOTwork
     root hsimple.C

Good luck!

---

### Post by Schrodinger on 2007-07-17
I have run into a very interesting problem trying to get ROOT/AliROOT to compile on my system. I install the necessary libraries the make goes fine, then when I 'make install'- my entire system crashes. (I have had to reinstall Ubuntu on my laptop about 4 times now because of this. ) I suspect that it has something to do with the OpenGL Libraries but cannot put my finger on it. Unfortunately, I really need ROOT and AliROOT for my research.

:guitar:

Any thoughts?

---

### Post by Schrodinger on 2007-07-17
Ah, just found this, here's a solution if you like binaries. 

[http://mirror.phy.bnl.gov/debian-root/](http://mirror.phy.bnl.gov/debian-root/)

---

### Post by jalirious on 2007-10-19
For lad.kocb, but feel free to shout out.

configure - fail - install xlibs-dev - configures.

make -

fails - g++ not recognised

installed g++ (synaptic & 7.10 disc)

g77 not recognised

installed g77

make error;

g++ -m32 -O2  -o bin/cint cint/main/cppmain.o \
                   -Llib -lCint -lm -ldl -rdynamic
lib/libCint.so: undefined reference to `G__getvirtualbaseoffset'
lib/libCint.so: undefined reference to `G__baseconstructorwp'
lib/libCint.so: undefined reference to `G__isanybase'
lib/libCint.so: undefined reference to `G__find_virtualoffset'
lib/libCint.so: undefined reference to `G__basedestructor'
lib/libCint.so: undefined reference to `G__ispublicbase'
lib/libCint.so: undefined reference to `G__baseconstructor'
lib/libCint.so: undefined reference to `G__publicinheritance'
lib/libCint.so: undefined reference to `G__inheritclass'
collect2: ld returned 1 exit status
make: *** [bin/cint] Error 1

install?


Incidentally, i386 & gutsy. Oh, and adding the repository to sources list didn't work as an alternative (after sudo su, apt-get update)

Reading package lists... Done
W: GPG error: [http://mirror.phy.bnl.gov](http://mirror.phy.bnl.gov) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7AD9343B6620D4F5
W: You may want to run apt-get update to correct these problems

idea?

---

### Post by jalirious on 2007-10-19
Disregard that. I noticed that when redoing the sources.list 'apt-get' that it was reading those libraries. Ignore the warning. 5.16 installed on my fresh gutsy in a heartbeat. May the Spaghetti Monster look kindly on Christian Holm!

[http://mirror.phy.bnl.gov/debian-root/](http://mirror.phy.bnl.gov/debian-root/)

---

### Post by dougleduck on 2007-10-20
Well I just installed no problem. Succesfully runs the .C files I've written. Success! 

Thanks.

---

### Post by jalirious on 2007-10-22
I had a problem running an old root program of mine to test the root 5.16 installation.

To get past these I had to update antiquated headers (new c++ compiler), installed cmake and most of the Minuit packages. tarra

---

### Post by dreamlusion on 2008-04-29
I'm running Xubuntu 8.04 and did not try tha prebuilt package so I had to install manually. There were some dependencies that the configure script did not catch.

x11proto-xext-dev
libxft-dev
libxext-dev

---

### Post by ThinkerR on 2008-05-02
Hi,

I am new to linux and i have been trying to install root on Ubuntu 8.04. I'm having some problems with the opengl viewer of root.

First I've installed the package "sudo apt-get install root-system" and the package was working fine until I tried to launch a geometry file and selected "view with opengl". Indeed I got an error in the terminal:
"Error in <TUnixSystem::DynamicPathName>: RGL[.so | .sl | .dl | .a | .dll] does not exist in .::/usr/lib/root/5.17
Warning in <TCanvas::TPad::CreateViewer3D>: Cannot create 3D viewer of type: ogl
"
So I've removed the package "sudo apt-get autremove root-system" and I've downloaded the source file ([ftp://root.cern.ch](ftp://root.cern.ch) /root/root_v5.18.00.source.tar.gz). I've also downloaded the MesaOpenGL file on ([ftp://root.cern.ch/root/opengl/Mesa.Linux.tar.gz](ftp://root.cern.ch/root/opengl/Mesa.Linux.tar.gz)). After some "gunzip" and "tarxfv" i went to the new root directory and typed: "./configure --prefix=/usr/local --with-opengl-incdir=/home/benjamin/Mesa/include/ --with-opengl-libdir=/home/benjamin/Mesa/lib/"
Then "make". After some missing packages (g77, g++, x11proto-xext-dev, libxft-dev, libxext-dev and some others), the make process stopped with:
"ftgl/src/FTExtrdGlyph.cxx: In constructor «FTExtrdGlyph::FTExtrdGlyph(FT_GlyphSlotRec_*, float, bool)»:
ftgl/src/FTExtrdGlyph.cxx:47: erreur: invalid conversion from «unsigned int» to «GLenum»
ftgl/src/FTExtrdGlyph.cxx:47: erreur:   initializing argument 1 of «void glBegin(GLenum)»
ftgl/src/FTExtrdGlyph.cxx:71: erreur: invalid conversion from «unsigned int» to «GLenum»
ftgl/src/FTExtrdGlyph.cxx:71: erreur:   initializing argument 1 of «void  glBegin(GLenum)»
make: *** [ftgl/src/FTExtrdGlyph.o] Erreur 1"

I tried to manipulate this file and succeeded. But then there was another one and on and on until I fell on a file I couldn't change because it began to be a little too complicated for me.

I am beginning to lose hope.

Help :(

---

### Post by Catalyst2Death on 2008-05-02
Is there no way that you can use the repositories?  I understand that they aren't the latest version, but they're certainly stable, and *A LOT* of the code written in later versions is backwards compatible.

If you do decide to go through the repositories, then you may have to install the opengl plugin separately.

If using the repositories is not an option, and you must install from source, then there are some things you can do to make it run smoother.

First, follow the instructions here:
[http://root.cern.ch/root/Install.html](http://root.cern.ch/root/Install.html)

I'm assuming your running bash, so when you seed commands with two different versions, you want to choose the sh one, NOT the csh version.

run ./configure without a prefix directory, and then set up the environment variables to link to where ever the compiled directory lives.  You can write a script to set up these variables, or you can append them to your .bashrc file.  Using a setup script is more versatile because you can have multiple versions of root on the same machine, ready to go.  This is nice if you are doing legacy analyses, but also want to begin work using newer tools.

My generic root start script looks like this:
```

#Setup root 5.18
unset root
# redefine ROOTSYS to point to 518
export ROOTSYS=<path to root 5.18>/root518

# redefine LD_LIBRARY_PATH from scratch
unset LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$ROOTSYS/lib"

alias root="$ROOTSYS/bin/root"
export PATH="$ROOTSYS/bin:${PATH}"
hash -r

```


the section of the install procedures relevant to openGL is here:
> Installing optional add-on libraries
If you want to compile the ROOT optional add-on libraries to handle True Type fonts, OpenGL graphics, SRP authentication, MySQL access, RFIO access and event generator interfaces (Pythia, Pythia6 and Venus) you can either specify the options as environment variables. For example:

  # Used during build of ROOT can be overridden in ./configure
  export ROOTBUILD=debug      # see $ROOTSYS/README/BUILDSYSTEM
  export CERNLIB=~/cernlib    # must contain libpacklib.a libkernlib.a
  export RFIO=~/shift/lib     # CERN's SHIFT library, must
                              # contain libshift.a
  export TTF=~/ttf            # must contain fonts/ (and possibly
                              # include/ lib/)
  export OPENGL=~/Mesa        # must contain include/ lib/
  export SRP=~/src/srp        # must contain include/ lib/
  #export AFS=                # must contain include/ lib/
  #export XPM=                # must contain libXpm
  #export MYSQL=              # must contain include/ lib/
  #export PYTHIA=             # must contain libPythia
  #export PYTHIA6=            # must contain libPythia6
  #export VENUS=              # must contain libVenus
  #export STAR=yes            # to build the STAR contrib library

The ROOTBUILD environment variable is special and architecture dependent. To get an idea of which values it can take, take a look in the config/Makefile.<architecture> corresponding to your architecture. 

getting root to work is sort of finicky, but when its all up and running it is certainly worth the effort!

---

### Post by cthunter on 2008-05-14
Okay, I've got yet more issues on compiling ROOT on my amd64 box. Hopefully some of you guys can help me here.

**What I want:**
ROOT v5.18 compiled with OpenGL and QT support.

I was going to install it in /usr/local/root/root518, but I'm compiling a copy without the --prefix flag. I want to set up the environment manually, say, with a launcher /usr/bin/root518 that sets up my environment for me at each launch. That way I can have multiple simultaneous copies of root installed in the future.

**What I did:**
- Grabbed the source tarball from root.cern.ch
```

$ ./configure --enable-opengl --enable-qt
$ make

```

The configure script runs perfectly, and the compile completes, but the linker fails on the Mathmore library. Here's the error I get:
```


...(snip)...

g++ -shared -Wl,-soname,libMathMore.so -m64 -O2 -o lib/libMathMore.so mathmore/src/Chebyshev.o mathmore/src/Derivator.o mathmore/src/GSLDerivator.o mathmore/src/GSLIntegrator.o mathmore/src/GSLInterpolator.o mathmore/src/GSLMCIntegrator.o mathmore/src/GSLMinimizer.o mathmore/src/GSLNLSMinimizer.o mathmore/src/GSLRndmEngines.o mathmore/src/GSLRootFinder.o mathmore/src/GSLRootFinderDeriv.o mathmore/src/GSLRootHelper.o mathmore/src/GSLSimAnMinimizer.o mathmore/src/GSLSimAnnealing.o mathmore/src/Interpolator.o mathmore/src/KelvinFunctions.o mathmore/src/Minimizer1D.o mathmore/src/ParamFunction.o mathmore/src/Polynomial.o mathmore/src/QuantFuncMathMore.o mathmore/src/RootFinderAlgorithms.o mathmore/src/SpecFuncMathMore.o mathmore/src/G__MathMore.o /usr/lib64/libgsl.a /usr/lib64/libgslcblas.a
[B]/usr/bin/ld: /usr/lib64/libgslcblas.a(sasum.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib64/libgslcblas.a: could not read symbols: Bad value[/B]
collect2: ld returned 1 exit status
make: *** [lib/libMathMore.so] Error 1
make: *** Waiting for unfinished jobs....
==> lib/libMathCore.so done

...(snip)...

```

So I need a gsl compiled with -fPIC. I installed gsl through synaptic, but apparently it wasn't compiled by the Ubuntu folks with that flag (I guess it's important on 64bit boxes?). I can recompile my own copy and install it manually, but then how do I get synaptic to know about it so it doesn't clobber my custom gsl installation in the future?

Or is there a way to get around this without compiling a custom version of gsl? I could add the **--disable-mathmore** flag to the configure command, but since I didn't specifically ask for mathmore in the configure process and it brought it in anyway, means that it's probably a part of the standard functionality of ROOT and I shouldn't disable it if I want a somewhat "standard" installation. At least I think that would be the case. Any ideas?

cheers,
Travis

---

### Post by cthunter on 2008-05-20
Well, I got the ROOT package from BNL's repo and it seems to work for me.

---

### Post by joanindo on 2008-05-22
you don't need to compile ROOT from source to save you time.
all you have to do is just download the pre-compiled program then run it.
to be more details:

goto: [http://root.cern.ch/root/Version518.html](http://root.cern.ch/root/Version518.html)
and download the program according to your architecture (32 or 64 bits)
and your platform, in this case i choose linux with 32 bits arch.
and download: [ftp://root.cern.ch/root/root_v5.18.00.Linux.slc4.gcc3.4.tar.gz](ftp://root.cern.ch/root/root_v5.18.00.Linux.slc4.gcc3.4.tar.gz)

and do these commands:
tar xzvf root_v5.18.00.Linux.slc4.gcc3.4.tar.gz
sudo mv root /usr/local

make a file named "root" and put these codes inside it:
export ROOTSYS=/usr/local/root
$ROOTSYS/bin/root $1 $2 $3 $4

then do these commands:
chmod a+rx root
sudo mv root /usr/local/bin

that's it. you're done.

in my case i install some programming languages by using this command:
sudo apt-get install build-essential g++ g77 gfortran

good luck!

---

### Post by juicyjuice on 2008-08-01
Hi, 

I had this problem with amd64 ubuntu.  I fixed it by installing GSL 1.11 by source with the following ./configure command:

./configure --prefix=/usr --enable-shared --with-pic

I also edited the makefile accordingly:

CC = gcc
CFLAGS = -g -O2 -m64 -fPIC
CPP = gcc -E 
CPPFLAGS = -m64 -fPIC

which involved adding -m64 -fPIC to CFLAGS and CPPFLAGS.  I think it was actually the m64 that was the problem, but I'm too lazy to go through the makefile again, and this DOES work.

Also, installing ROOT from source is better than using prebuilt binaries, IMO.  Half the people I work with in particle astrophysics automatically program most of their stuff to search for the ROOTSYS directory and use libraries, source, and binaries from there.  Some of the binaries I've used in the past put libs in /usr/lib and includes in /usr/include, etc... and it's just a pain in the butt rewriting makefile after makefile.  If you are going to work with other people's source code, I recommend installing by source.  Also, since ROOT is often updated, broken, fixed, etc... with additions and changes from version to version, it's sometimes a good idea to have multiple root installations in an organized manner.  As an example, I have 5.16 and 5.20 (with a softlink from "root" to "root_520" as the default) both installed on my machine.  

Thanks

---

### Post by yo_marcus on 2008-10-29
> **ThinkerR said:**
> Hi,

I am new to linux and i have been trying to install root on Ubuntu 8.04. I'm having some problems with the opengl viewer of root.

First I've installed the package "sudo apt-get install root-system" and the package was working fine until I tried to launch a geometry file and selected "view with opengl". Indeed I got an error in the terminal:
**"Error in <TUnixSystem::DynamicPathName>: RGL[.so | .sl | .dl | .a | .dll] does not exist in .::/usr/lib/root/5.17**

I solved this "problem" looking for "Minuit" in synaptic, using the root repository (that with root5.17, I mean [http://mirror.phy.bnl.gov/debian-root/ubuntu/](http://mirror.phy.bnl.gov/debian-root/ubuntu/)) ;)

---

### Post by 080729jk on 2008-10-30
That sounds fine, right? It should help the casters and even though hunters don't stack spirit, wow gold just means we won't get the extra boost of regen. [**world of warcraft gold**](http://www.oofay.com/)That's probably what Blizzard thought too.The current estimation is that any hunter with less than 300 intellect is being negatively affected by the change.[**world of warcraft gold**](http://www.oofay.com/) Despite some claims that only lowbie hunters will be affected, [** buy wow gold **](http://www.oofay.com/)many 70s are being hard-hit. Why are we upset that we might have to start choosing intellect enchants rather than focusing on other stats? A few simple reasons. Yes, we are a mana class. It was not always this way, and perhaps it should not be this way.wow gold We are much more like rogues and warriors than mages or warlocks. Paladins use mana because they are hybrids; [** buy wow gold **](http://www.oofay.com/)melee casters with holy powers. Regardless, [**cheap wow gold**](http://www.oofay.com/)if we stack intellect with high priority, we lose a ton of damage. Casters don't.

---

### Post by fawadzafar on 2008-12-05
I am new in ubuntu.please guide me to install C++ and frotrann77 in ubuntu.

---

### Post by juicyjuice on 2008-12-12
> **fawadzafar said:**
> I am new in ubuntu.please guide me to install C++ and frotrann77 in ubuntu.

You'll probably want gfortran

use:
sudo apt-get install build-essential
sudo apt-get install gfortran

build-essential installs a lot of what you will need if it's not already installed for c++.  gfortran replaces g77 which stopped development.

---

### Post by Sorivenul on 2008-12-12
> **fawadzafar said:**
> I am new in ubuntu.please guide me to install C++ and frotrann77 in ubuntu.
I read the recommendation for gfortran, however this, to my knowledge only includes Fortran95 support. g77 would be the Fortran compiler you are looking for.

---

