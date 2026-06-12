---
title: "compile fortran subroutine using matlab via mex"
date: 2009-05-08
forum: Education &amp; Science
---

### Post by subjugater on 2009-05-08
Hi, guys,

I am now trying to compile a fortran subroutine using matlab by building MEX-file first. My matlab version is a little old (2007b). I come across the following error, when I was using command mex in the command window:

> >> mex yprimef.F yprimefg.F
Warning: You are using gcc version "4.2.4".  The earliest gcc version supported
with mex is "4.0.0".  The latest version tested for use with mex is "4.2.0".
To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org) 
eval: 1: g95: not found

    mex: compile of 'yprimef.F' failed.

??? Error using ==> mex at 208
Unable to complete successfully.

Is there anyone encountered same issue? 

I checked online and found that even the newest version matlab can only support up to gcc version '4.2.3'. This basically means that it won't work if I choose to install the new version matlab. Hence, I guess, the way to sort it out might be choose an older version gcc, say 4.1.0 for example. Does anyone know how to do that?

Any comments are appreciated. Thanks.

---

### Post by subjugater on 2009-05-09
Anybody who knows how to choose the compiler? For example, enforce the system to use gcc-4.1.0, instead of gcc-4.2.4. Thanks.

---

### Post by melissawm on 2009-05-15
Just did this.

1) In my case, I chose to install gcc-4.1:

```
sudo apt-get install gcc-4.1
```

Don't forget to also install gfortran.

2) Fire up MATLAB, do

```
mex -setup
```

and choose to use "mexopts.sh" ( in my case, it was option #3)

3) Open ~/.matlab/mexopts.sh (using emacs, vim, gedit... whatever - sometimes it is under ~/.matlab/R2007b/mexopts.sh - assuming R2007b is your matlab version) and look inside the file for the part corresponding to your architecture; in my case, I'm using Ubuntu 64bit and so I modified this part:

```

#----------------------------------------------------------------------------
            ;;
        glnxa64)
#----------------------------------------------------------------------------
            RPATH="-Wl,-rpath-link,$TMW_ROOT/bin/$Arch"
            CC='gcc'
            CFLAGS='-ansi -D_GNU_SOURCE -fexceptions'
            CFLAGS="$CFLAGS -fPIC -fno-omit-frame-pointer -pthread"
            CLIBS="$RPATH $MLIBS -lm -lstdc++"
            COPTIMFLAGS='-O -DNDEBUG'
            CDEBUGFLAGS='-g'
#
            CXX='g++'
            CXXFLAGS='-ansi -D_GNU_SOURCE'
            CXXFLAGS="$CXXFLAGS -fPIC -fno-omit-frame-pointer -pthread"
            CXXLIBS="$RPATH $MLIBS -lm"
            CXXOPTIMFLAGS='-O -DNDEBUG'
            CXXDEBUGFLAGS='-g'
#
#
            FC='g95'
            FFLAGS='-fexceptions'
            FFLAGS="$FFLAGS -fPIC -fno-omit-frame-pointer"
            FLIBS="$RPATH $MLIBS -lm"
            FOPTIMFLAGS='-O'
            FDEBUGFLAGS='-g'
#
            LD="$COMPILER"
            LDEXTENSION='.mexa64'
            LDFLAGS="-pthread -shared -Wl,--version-script,$TMW_ROOT/extern/lib/$Arch/$MAPFILE -Wl,--no-undefined"
            LDOPTIMFLAGS='-O'
            LDDEBUGFLAGS='-g'
#
            POSTLINK_CMDS=':'

```

to read

```

#----------------------------------------------------------------------------
            ;;
        glnxa64)
#----------------------------------------------------------------------------
            RPATH="-Wl,-rpath-link,$TMW_ROOT/bin/$Arch"
            [COLOR=Red]CC='gcc-4.1'[/COLOR]
            CFLAGS='-ansi -D_GNU_SOURCE -fexceptions'
            CFLAGS="$CFLAGS -fPIC -fno-omit-frame-pointer -pthread"
            CLIBS="$RPATH $MLIBS -lm -lstdc++"
            COPTIMFLAGS='-O -DNDEBUG'
            CDEBUGFLAGS='-g'
#
       [COLOR=Red]     CXX='g++-4.1'[/COLOR]
            CXXFLAGS='-ansi -D_GNU_SOURCE'
            CXXFLAGS="$CXXFLAGS -fPIC -fno-omit-frame-pointer -pthread"
            CXXLIBS="$RPATH $MLIBS -lm"
            CXXOPTIMFLAGS='-O -DNDEBUG'
            CXXDEBUGFLAGS='-g'
#
#
[COLOR=Red]            FC='gfortran'[/COLOR]
            FFLAGS='-fexceptions'
            FFLAGS="$FFLAGS -fPIC -fno-omit-frame-pointer"
            FLIBS="$RPATH $MLIBS -lm"
            FOPTIMFLAGS='-O'
            FDEBUGFLAGS='-g'
#
            LD="$COMPILER"
            LDEXTENSION='.mexa64'
            LDFLAGS="-pthread -shared -Wl,--version-script,$TMW_ROOT/extern/lib/$Arch/$MAPFILE -Wl,--no-undefined"
            LDOPTIMFLAGS='-O'
            LDDEBUGFLAGS='-g'
#
            POSTLINK_CMDS=':'

```

4) Restart matlab.

You should be able to compile your mex now. 

Good luck! :D

---

### Post by Jessehk on 2009-08-05
Thanks melissawm.

It's strange that TMW advises that MATLAB R2009a is compatible with this release of Ubuntu ("Ubuntu 8 and above" [http://www.mathworks.com/support/sysreq/current_release/linux.html](http://www.mathworks.com/support/sysreq/current_release/linux.html)) while the default GCC version is 4.3. I'm just glad that the Ubuntu/Debian packagers are still supporting some older versions of GCC.

---

### Post by uranoscopus on 2013-01-29
The error was just related to fortran compiler. Concerning the Gcc it was just a warning, so you can try to compile it without any change on gcc and just changing your default compiler in the mex-options.
It works for me.
Cheers,
Antonio

---

### Post by howefield on 2013-01-29
Old thread closed.

---

