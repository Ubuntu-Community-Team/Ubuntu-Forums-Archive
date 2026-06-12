---
title: "Cern Root 5.26"
date: 2009-12-29
forum: Education &amp; Science
---

### Post by paolomarco on 2009-12-29
Hi all, this is my first post !
 
I'm trying to update my ubuntu in order to compile root in a good way... 

BUT I MISS SOME LIBRARIES !
 
after some efforts this is what I obtain: 

Configuring for linuxx8664gcc
Checking for GNU Make version >= 3.79.1 ... ok
Checking for C compiler ... gcc
Checking for C++ compiler ... g++
Checking for linker (LD) ... g++
Checking for F77 compiler ... gfortran
Checking for libX11 ... /usr/lib64
Checking for X11/Xlib.h ... /usr/include
Checking for X11/Xft/Xft.h ... /usr/include
Checking for X11/extensions/shape.h ... /usr/include
Checking for libXpm ... /usr/lib64
Checking for libXft ... /usr/lib64
Checking for libXext ... /usr/lib64
Checking whether to build included libfreetype6 ... yes
Checking whether to build included libftgl ... yes
Checking whether to build included libpcre ... yes
Checking whether to build included zlib ... yes
Checking for ncurses.h, or curses.h ... /usr/include
Checking for libncurses, or libcurses ... /usr/lib64
Checking for GL/gl.h ... /usr/include
Checking for libGL, or libMesaGL ... /usr/lib64
Checking for libGLU, or libMesaGLU ... /usr/lib64
Checking for GL/glew.h ... /usr/include
Checking for libGLEW ... /usr/lib64
Checking whether to build included GLEW ... no
Checking for mysql_config ... /usr/bin/mysql_config
Checking for libmysqlclient version >= 3.23.* ... ok
Checking for mysql.h ... /usr/include/mysql
Checking for occi.h ... no
Checking for libclntsh, or oci ... no
Checking for libocci, or oraocci10 ... no
Checking for libpq-fe.h ... /usr/include/postgresql
Checking for libpq ... /usr/lib64
Checking for sql.h ... no
Checking for libsqlod ... no
Checking for sqlext.h ... /usr/include
Checking for libiodbc, libodbc, or odbc32 ... /usr/lib64
Checking for rfio_api.h ... no
Checking for librfio, libshift, shiftmd, or shift ... no
Checking for rfio_api.h ... no
Checking for stager_api.h ... no
Checking for libshift, shiftmd, or shift ... no
Checking for gfal_api.h ... no
Checking for libgfal ... no
Checking for G4Navigator.hh ... no
Checking for libG4navigation ... no
Checking for CLHEP/Vector/Rotation.h ... no
Checking for ApMon.h ... no
Checking for libapmoncpp ... no
Checking for fftw3.h ... /usr/include
Checking for libfftw3, or libfftw3-3 ... /usr/lib64
Checking for gvc.h ... /usr/include/graphviz
Checking for libgvc, or gvc ... /usr/lib64
Checking for libgraph, or graph ... /usr/lib64
Checking for libcdt, or cdt ... /usr/lib64
Checking for libpathplan, or pathplan ... /usr/lib64
Checking for libgvplugin_dot_layout, or gvplugin_dot_layout ... /usr/lib64/graphviz
Checking for libPythia6 ... no
Checking for Pythia.h ... no
Checking for libpythia8 ... no
Checking for dcap.h ... no
Checking for libdcap ... no
Checking for chirp_client.h ... no
Checking for libchirp_client ... no
Checking for hdfs.h ... no
Checking for jni.h ... no
Checking for libhdfs ... no
Checking for libjvm ... no
Checking for dns_sd.h ... no
Checking for libdns_sd ... no
Checking for libglite-api-wrapper ... no
Checking for gapiUI.h ... no
Checking for libgapiUI ... no
Checking for jpeglib.h ... /usr/include
Checking for png.h ... /usr/include
Checking for tiffio.h ... /usr/include
Checking for gif_lib.h ... /usr/include
Checking for libjpeg ... /usr/lib64
Checking for libtiff ... /usr/lib64
Checking for libungif ... /usr/lib64
Checking for libz ... /usr/lib64
Checking for libpng ... /usr/lib64
Checking whether to build included libAfterImage ... yes
Checking for ldap.h ... /usr/include
Checking for libldap ... /usr/lib64
Checking for liblber ... /usr/lib64
Checking for Python.h ... no
Checking for python2.6, libpython2.6, libpython, python, or Python ... no
Checking for xml2-config ... /usr/bin/xml2-config
Checking for libxml2 version >= 2.4.x ... ok
Checking whether to build xrootd ... yes
Checking for libssl ... /usr/lib64
Checking for libcrypto ... /usr/lib64
Checking for openssl/bio.h ... /usr/include
Checking for openssl/blowfish.h ... /usr/include
Checking for openssl/err.h ... /usr/include
Checking for openssl/pem.h ... /usr/include
Checking for openssl/rand.h ... /usr/include
Checking for openssl/rsa.h ... /usr/include
Checking for t_server.h ... no
Checking for libsrp ... no
Checking for libgmp ... /usr/lib64
Checking for libmisc ... no
Checking for pwauth.h ... no
Checking for shadow passwords ... yes
Checking for gsl/gsl_version.h ... /usr/include
Checking for GSL version >= 1.8 ... ok
Checking for libgsl, gslML, or gsl ... /usr/lib64
Checking for libgslcblas, gslcblasML, gslcblas, or cblas ... /usr/lib64
Checking whether /usr/lib64/libgsl.a is compiled with -fPIC ... yes
Checking whether /usr/lib64/libgslcblas.a is compiled with -fPIC ... no
Checking whether to build libMathMore ... no
Checking whether to build libGenVector ... yes
Checking whether to build CINT5 ... yes
Checking whether to build CINT7 ... no
Checking whether to build libCintex ... yes
Checking whether to build libReflex ... yes
Checking whether to build libRooFit ... no
Checking whether to build libMinuit2 ... no
Checking whether to build libUnuran ... no
Checking whether to build libGdml ... no
Checking whether to build libTable ... no
Checking whether to build libTMVA ... yes
Checking whether to build libMemStat ... yes
Checking for Clarens support ... yes
Checking for PEAC support ... yes
Generating cint dictionaries.
Checking whether setresuid declared in /usr/include/unistd.h ... yes
Writing config/Makefile.config ... done
Writing config/Makefile.comp ... done
Writing include/RConfigure.h ... done
Writing include/RConfigOptions.h ... done
Writing bin/root-config ... done
Writing etc/system.rootrc ... done
Writing etc/system.rootauthrc ... done
Writing etc/system.rootdaemonrc ... done
Writing etc/root.mimes ... done
Writing etc/daemons/rootd.rc.d ... done
Writing etc/daemons/rootd.xinetd ... done
Writing etc/daemons/proofd.rc.d ... done
Writing etc/daemons/proofd.xinetd ... done
Writing etc/daemons/xrootd.rc.d ... done
Writing etc/daemons/olbd.rc.d ... done
Writing bin/memprobe ... done
Writing build/misc/root-help.el ... done
Writing macros/html.C ... done
Writing bin/thisroot.sh ... done
Writing bin/thisroot.csh ... done
Writing bin/genreflex ... done
Writing bin/genreflex-rootcint ... done
Writing config.status ... done

Enabled support for asimage, astiff, builtin_afterimage, builtin_ftgl, builtin_freetype, builtin_pcre, builtin_zlib, cint5, cintex, clarens, editline, exceptions, fftw3, gviz, genvector, ldap, memstat, mysql, odbc, opengl, peac, pgsql, reflex, shadowpw, shared, ssl, tmva, xft, xml, xrootd.

To build ROOT type:


   make 
   make install 
 
What I need is to know which software/library belong those are marked with no.... 
 
I need to compile RooFit and Minuit2 at least !

THANKS A LOT ! :KS

---

### Post by paolomarco on 2009-12-29
JUST TO HELP I'm just coping what I don't have,
to make things more readable:



Checking whether to build included GLEW ... no

Checking for occi.h ... no
Checking for libclntsh, or oci ... no
Checking for libocci, or oraocci10 ... no

Checking for sql.h ... no
Checking for libsqlod ... no

Checking for rfio_api.h ... no
Checking for librfio, libshift, shiftmd, or shift ... no
Checking for rfio_api.h ... no
Checking for stager_api.h ... no
Checking for libshift, shiftmd, or shift ... no
Checking for gfal_api.h ... no
Checking for libgfal ... no
Checking for G4Navigator.hh ... no
Checking for libG4navigation ... no
Checking for CLHEP/Vector/Rotation.h ... no
Checking for ApMon.h ... no
Checking for libapmoncpp ... no

Checking for libPythia6 ... no
Checking for Pythia.h ... no
Checking for libpythia8 ... no
Checking for dcap.h ... no
Checking for libdcap ... no
Checking for chirp_client.h ... no
Checking for libchirp_client ... no
Checking for hdfs.h ... no
Checking for jni.h ... no
Checking for libhdfs ... no
Checking for libjvm ... no
Checking for dns_sd.h ... no
Checking for libdns_sd ... no
Checking for libglite-api-wrapper ... no
Checking for gapiUI.h ... no
Checking for libgapiUI ... no

Checking for Python.h ... no
Checking for python2.6, libpython2.6, libpython, python, or Python ... no
Checking for xml2-config ... /usr/bin/xml2-config

Checking for t_server.h ... no
Checking for libsrp ... no

Checking for libmisc ... no
Checking for pwauth.h ... no

Checking whether /usr/lib64/libgslcblas.a is compiled with -fPIC ... no
Checking whether to build libMathMore ... no

Checking whether to build CINT7 ... no

Checking whether to build libRooFit ... no
Checking whether to build libMinuit2 ... no
Checking whether to build libUnuran ... no
Checking whether to build libGdml ... no
Checking whether to build libTable ... no

It would be fantastic if anyone could know what libraries I should add to compile it...

I'm usung UBUNTU 9.10 o a 64 bit machine

---

### Post by gunksta on 2009-12-29
Disclaimer - I have never compiled or used Root. With a larger, more complex program (with lots of dependencies) I usually recommend that users install the version in the repositories, unless there is a clear and compelling need for a newer version.

Ok, now to fix your problem, if you decide to persist with compiling it yourself.

You need to install a bunch of -dev files. For example, you get this:

Checking for Python.h ... no
Checking for python2.6, libpython2.6, libpython, python, or Python ... no

That it can't find Python.h (header file) tells me that you don't have the development package installed for python. Looking at the next line, it appears to want python 2.6, which is still pretty much the standard these days.

You can fix this error with - 

```
sudo apt-get install python2.6-dev
```

You need to go through each of these errors and figure out what package they belong to, and install the corresponding "-dev" file. Assuming that the versions of these dependencies are all new enough, the program will stop giving you these error messages.

WARNING - Python 2.6 is easily found in just about every distro on earth right now. I don't recognize all of these, and some of these may be esoteric or fast moving packages and the version needed by ROOT may be newer than that found in the repo. If that is the case, you get to compile the dependencies manually too. If this over-writes an older file this could break something else, and so on and so forth. Compiling lots of dependencies can get tricky. If you don't know what you are doing I advise you to do this on a test machine / virtual machine first, so you can make sure everything works before doing this on your main system.

You should also install and learn how to use checkinstall. (sudo apt-get install checkinstall). You can learn how to use it with man checkinstall

Now, you need to find these other programs. apt-cache is going to be useful here. For example, I don't know what sql.h is attached to. But, I can find it with:

apt-cache search sql.h

I notice that the Haskell extensions to Postgres pop up. Assuming that this looks sane (does this app use postgres?), I would probably assume that I need to install the relevant file AND the relevant -dev files.

Hope this gets you started, or convinces you to apt-get install.

:popcorn:

---

### Post by doas777 on 2009-12-29
you may need to install build-essential and the sun java runtime as well.

---

### Post by gunksta on 2009-12-29
Correction - I looked on the Ubuntu package search, and I apparently goobered something up. It looks like sql.h is actually part of unixodbc or iodbc. You don't really want both of these installed, so you will need to decide which you want to use / configure.

Like I said. Compiling can be tricky.

---

### Post by gunksta on 2009-12-29
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

This is a very useful link. At the bottom of the page you can search within packages. It's probably easier to do it this way than to use apt-cache.

---

### Post by paolomarco on 2011-09-12
Thanks a lot for your help !

---

