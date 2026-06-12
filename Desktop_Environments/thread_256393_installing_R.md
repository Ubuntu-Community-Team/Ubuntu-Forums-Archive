---
title: "installing R"
date: 2006-09-12
forum: Desktop Environments
---

### Post by mozkaynak on 2006-09-12
Hi,
I need to use R which is a statistics software for my research. I have Xubuntu on my trash.
I installed the package prepared for dappler ([http://cran.cnr.berkeley.edu/bin/linux/ubuntu/dapper/r-base_2.3.1.orig.tar.gz)](http://cran.cnr.berkeley.edu/bin/linux/ubuntu/dapper/r-base_2.3.1.orig.tar.gz)).

After unpacking the package I wanted to install it and run ./configure .

I got the following error message: > configure: error: no acceptable C compiler found in $PATH


I would appreciate any help. 
the followings are the stuff than were seen on the terminal and the content of configure.log file:

> mozkaynak@ozkaynak:~/stat692/R-2.3.1$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
loading site script './config.site'
loading build specific script './config.site'
checking for pwd... /bin/pwd
checking whether builddir is srcdir... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gawk... no
checking for mawk... mawk
checking for egrep... grep -E
checking whether ln -s works... yes
checking for ranlib... :
checking for bison... no
checking for byacc... no
checking for ar... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... /bin/sed
checking for less... /usr/bin/less
checking for perl... /usr/bin/perl
checking whether perl version is at least 5.004... yes
checking for dvips... no
checking for tex... no
checking for latex... no
configure: WARNING: you cannot build DVI versions of the R manuals
checking for makeindex... no
checking for pdftex... no
checking for pdflatex... no
configure: WARNING: you cannot build PDF versions of the R manuals
checking for $(SHELL)... no
checking for $(top_srcdir)/tools/missing... no
checking for makeinfo... no
checking for makeinfo... no
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for gzip... /bin/gzip
checking for firefox... /usr/bin/firefox
using default browser ... /usr/bin/firefox
checking for acroread... no
checking for acroread4... no
checking for xpdf... no
checking for gv... no
checking for gnome-gv... no
checking for ggv... no
checking for kghostview... no
checking for open... /usr/bin/open
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
mozkaynak@ozkaynak:~/stat692/R-2.3.1$ make
bash: make: command not found
mozkaynak@ozkaynak:~/stat692/R-2.3.1$ ./make
bash: ./make: No such file or directory
mozkaynak@ozkaynak:~/stat692/R-2.3.1$ ./make install
bash: ./make: No such file or directory
mozkaynak@ozkaynak:~/stat692/R-2.3.1$ make install
bash: make: command not found
mozkaynak@ozkaynak:~/stat692/R-2.3.1$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
loading site script './config.site'
loading build specific script './config.site'
checking for pwd... /bin/pwd
checking whether builddir is srcdir... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gawk... no
checking for mawk... mawk
checking for egrep... grep -E
checking whether ln -s works... yes
checking for ranlib... :
checking for bison... no
checking for byacc... no
checking for ar... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... /bin/sed
checking for less... /usr/bin/less
checking for perl... /usr/bin/perl
checking whether perl version is at least 5.004... yes
checking for dvips... no
checking for tex... no
checking for latex... no
configure: WARNING: you cannot build DVI versions of the R manuals
checking for makeindex... no
checking for pdftex... no
checking for pdflatex... no
configure: WARNING: you cannot build PDF versions of the R manuals
checking for $(SHELL)... no
checking for $(top_srcdir)/tools/missing... no
checking for makeinfo... no
checking for makeinfo... no
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for gzip... /bin/gzip
checking for firefox... /usr/bin/firefox
using default browser ... /usr/bin/firefox
checking for acroread... no
checking for acroread4... no
checking for xpdf... no
checking for gv... no
checking for gnome-gv... no
checking for ggv... no
checking for kghostview... no
checking for open... /usr/bin/open
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by R configure 2.3.1, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = ozkaynak
uname -m = i686
uname -r = 2.6.15-26-386
uname -s = Linux
uname -v = #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1796: checking build system type
configure:1814: result: i686-pc-linux-gnuoldld
configure:1822: checking host system type
configure:1836: result: i686-pc-linux-gnuoldld
configure:2366: checking for pwd
configure:2384: found /bin/pwd
configure:2397: result: /bin/pwd
configure:2404: checking whether builddir is srcdir
configure:2412: result: yes
configure:2417: checking for working aclocal
configure:2425: result: missing
configure:2430: checking for working autoconf
configure:2438: result: missing
configure:2443: checking for working automake
configure:2451: result: missing
configure:2456: checking for working autoheader
configure:2464: result: missing
configure:2469: checking for working makeinfo
configure:2477: result: missing
configure:2486: checking for gawk
configure:2515: result: no
configure:2486: checking for mawk
configure:2502: found /usr/bin/mawk
configure:2512: result: mawk
configure:2522: checking for egrep
configure:2532: result: grep -E
configure:2537: checking whether ln -s works
configure:2541: result: yes
configure:2589: checking for ranlib
configure:2616: result: :
configure:2632: checking for bison
configure:2661: result: no
configure:2632: checking for byacc
configure:2661: result: no
configure:2673: checking for ar
configure:2702: result: no
configure:2725: checking for a BSD-compatible install
configure:2780: result: /usr/bin/install -c
configure:2815: checking for sed
configure:2834: found /bin/sed
configure:2846: result: /bin/sed
configure:2865: checking for less
configure:2883: found /usr/bin/less
configure:2895: result: /usr/bin/less
configure:2917: checking for perl
configure:2935: found /usr/bin/perl
configure:2947: result: /usr/bin/perl
configure:2958: checking whether perl version is at least 5.004
configure:2969: result: yes
configure:3042: checking for dvips
configure:3075: result: no
configure:3087: checking for tex
configure:3120: result: no
configure:3132: checking for latex
configure:3165: result: no
configure:3179: WARNING: you cannot build DVI versions of the R manuals
configure:3186: checking for makeindex
configure:3219: result: no
configure:3231: checking for pdftex
configure:3264: result: no
configure:3276: checking for pdflatex
configure:3309: result: no
configure:3323: WARNING: you cannot build PDF versions of the R manuals
configure:3330: checking for $(SHELL)
configure:3363: result: no
configure:3330: checking for $(top_srcdir)/tools/missing
configure:3363: result: no
configure:3330: checking for makeinfo
configure:3363: result: no
configure:3330: checking for makeinfo
configure:3363: result: no
configure:3430: checking for unzip
configure:3448: found /usr/bin/unzip
configure:3460: result: /usr/bin/unzip
configure:3475: checking for zip
configure:3493: found /usr/bin/zip
configure:3505: result: /usr/bin/zip
configure:3520: checking for gzip
configure:3538: found /bin/gzip
configure:3550: result: /bin/gzip
configure:3567: checking for firefox
configure:3585: found /usr/bin/firefox
configure:3597: result: /usr/bin/firefox
configure:3613: result: using default browser ... /usr/bin/firefox
configure:3623: checking for acroread
configure:3656: result: no
configure:3623: checking for acroread4
configure:3656: result: no
configure:3623: checking for xpdf
configure:3656: result: no
configure:3623: checking for gv
configure:3656: result: no
configure:3623: checking for gnome-gv
configure:3656: result: no
configure:3623: checking for ggv
configure:3656: result: no
configure:3623: checking for kghostview
configure:3656: result: no
configure:3623: checking for open
configure:3641: found /usr/bin/open
configure:3653: result: /usr/bin/open
configure:3717: checking for gcc
configure:3746: result: no
configure:3797: checking for cc
configure:3826: result: no
configure:3839: checking for cc
configure:3885: result: no
configure:3938: checking for cl
configure:3967: result: no
configure:3981: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnuoldld
ac_cv_build_alias=i686-pc-linux-gnuoldld
ac_cv_env_BLAS_LIBS_set=
ac_cv_env_BLAS_LIBS_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPICFLAGS_set=
ac_cv_env_CPICFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXXPICFLAGS_set=
ac_cv_env_CXXPICFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DYLIB_LDFLAGS_set=
ac_cv_env_DYLIB_LDFLAGS_value=
ac_cv_env_DYLIB_LD_set=
ac_cv_env_DYLIB_LD_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FCFLAGS_set=
ac_cv_env_FCFLAGS_value=
ac_cv_env_FCPICFLAGS_set=
ac_cv_env_FCPICFLAGS_value=
ac_cv_env_FC_set=
ac_cv_env_FC_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_FPICFLAGS_set=
ac_cv_env_FPICFLAGS_value=
ac_cv_env_LAPACK_LIBS_set=
ac_cv_env_LAPACK_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBnn_set=
ac_cv_env_LIBnn_value=
ac_cv_env_MAIN_CFLAGS_set=
ac_cv_env_MAIN_CFLAGS_value=
ac_cv_env_MAIN_FFLAGS_set=
ac_cv_env_MAIN_FFLAGS_value=
ac_cv_env_MAIN_LDFLAGS_set=
ac_cv_env_MAIN_LDFLAGS_value=
ac_cv_env_MAIN_LD_set=
ac_cv_env_MAIN_LD_value=
ac_cv_env_MAKE_set=
ac_cv_env_MAKE_value=
ac_cv_env_R_BATCHSAVE_set=
ac_cv_env_R_BATCHSAVE_value=
ac_cv_env_R_BROWSER_set=
ac_cv_env_R_BROWSER_value=
ac_cv_env_R_PAPERSIZE_set=
ac_cv_env_R_PAPERSIZE_value=
ac_cv_env_R_PRINTCMD_set=
ac_cv_env_R_PRINTCMD_value=
ac_cv_env_SAFE_FFLAGS_set=
ac_cv_env_SAFE_FFLAGS_value=
ac_cv_env_SHLIB_CFLAGS_set=
ac_cv_env_SHLIB_CFLAGS_value=
ac_cv_env_SHLIB_CXXLDFLAGS_set=
ac_cv_env_SHLIB_CXXLDFLAGS_value=
ac_cv_env_SHLIB_CXXLD_set=
ac_cv_env_SHLIB_CXXLD_value=
ac_cv_env_SHLIB_FCD_set=
ac_cv_env_SHLIB_FCD_value=
ac_cv_env_SHLIB_FCLDFLAGS_set=
ac_cv_env_SHLIB_FCLDFLAGS_value=
ac_cv_env_SHLIB_FFLAGS_set=
ac_cv_env_SHLIB_FFLAGS_value=
ac_cv_env_SHLIB_LDFLAGS_set=
ac_cv_env_SHLIB_LDFLAGS_value=
ac_cv_env_SHLIB_LD_set=
ac_cv_env_SHLIB_LD_value=
ac_cv_env_TCLTK_CPPFLAGS_set=
ac_cv_env_TCLTK_CPPFLAGS_value=
ac_cv_env_TCLTK_LIBS_set=
ac_cv_env_TCLTK_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_r_arch_set=
ac_cv_env_r_arch_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnuoldld
ac_cv_host_alias=i686-pc-linux-gnuoldld
ac_cv_path_GETWD=/bin/pwd
ac_cv_path_PAGER=/usr/bin/less
ac_cv_path_PERL=/usr/bin/perl
ac_cv_path_R_BROWSER=/usr/bin/firefox
ac_cv_path_R_GZIPCMD=/bin/gzip
ac_cv_path_R_PDFVIEWER=/usr/bin/open
ac_cv_path_R_UNZIPCMD=/usr/bin/unzip
ac_cv_path_R_ZIPCMD=/usr/bin/zip
ac_cv_path_SED=/bin/sed
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_RANLIB=:
ac_cv_prog_egrep='grep -E'
r_cv_prog_perl_v5=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='$(SHELL) $(top_srcdir)/tools/missing aclocal'
ALLOCA=''
AR=''
ARFLAGS='rc'
AUTOCONF='$(SHELL) $(top_srcdir)/tools/missing autoconf'
AUTOHEADER='$(SHELL) $(top_srcdir)/tools/missing autoheader'
AUTOMAKE='$(SHELL) $(top_srcdir)/tools/missing automake'
AWK='mawk'
BITMAP_LIBS=''
BLAS_LIBS=''
BUILDDIR_IS_SRCDIR='yes'
BUILD_AQUA_FALSE=''
BUILD_AQUA_TRUE=''
BUILD_BZLIB_FALSE=''
BUILD_BZLIB_TRUE=''
BUILD_INCLUDED_LIBINTL=''
BUILD_LIBINTL_FALSE=''
BUILD_LIBINTL_TRUE=''
BUILD_PCRE_FALSE=''
BUILD_PCRE_TRUE=''
BUILD_XDR_FALSE=''
BUILD_XDR_TRUE=''
BUILD_ZLIB_FALSE=''
BUILD_ZLIB_TRUE=''
CATOBJEXT=''
CC=''
CFLAGS=''
COMPILE_FORTRAN_DOUBLE_COMPLEX_FALSE=''
COMPILE_FORTRAN_DOUBLE_COMPLEX_TRUE=''
CPICFLAGS=''
CPP=''
CPPFLAGS='-I/usr/local/include'
CXX=''
CXXCPP=''
CXXFLAGS=''
CXXPICFLAGS=''
C_VISIBILITY=''
DATADIRNAME=''
DEFS=''
DVIPS='false'
DYLIB_EXT=''
DYLIB_LD=''
DYLIB_LDFLAGS=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='grep -E'
EXEEXT=''
F77=''
F77_VISIBILITY=''
FALSE=''
FC=''
FCFLAGS=''
FCFLAGS_f90=''
FCFLAGS_f95=''
FCPICFLAGS=''
FFLAGS=''
FLIBS=''
FPICFLAGS=''
FW_VERSION=''
GENCAT=''
GETWD='/bin/pwd'
GLIBC21=''
GLIBC2=''
GMSGFMT=''
HAVE_ASPRINTF=''
HAVE_C99_COMPLEX=''
HAVE_FORTRAN_DOUBLE_COMPLEX=''
HAVE_POSIX_PRINTF=''
HAVE_SNPRINTF=''
HAVE_WPRINTF=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_INFO='$(PERL) $(top_srcdir)/tools/install-info.pl'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTOBJEXT=''
INTLBISON=''
INTLLIBS=''
INTLOBJS=''
INTL_LIBTOOL_SUFFIX_PREFIX=''
INTL_MACOSX_LIBS=''
JAVA=''
JAVAC=''
JAVA_HOME=''
JAVA_LD_LIBRARY_PATH=''
JAVA_LIBS=''
LAPACK_LDFLAGS=''
LAPACK_LIBS=''
LATEX='false'
LDFLAGS='-L/usr/local/lib'
LIBICONV=''
LIBINTL=''
LIBM=''
LIBOBJS=''
LIBR=''
LIBR_LDFLAGS=''
LIBS=''
LIBTOOL=''
LIBTOOL_DEPS=''
LIBnn='lib'
LN_S='ln -s'
LTLIBICONV=''
LTLIBINTL=''
LTLIBOBJS=''
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAIN_CFLAGS=''
MAIN_FFLAGS=''
MAIN_LD=''
MAIN_LDFLAGS=''
MAKE='make'
MAKEINDEX='false'
MAKEINFO='$(SHELL) $(top_srcdir)/tools/missing makeinfo'
MAKEINFO_CMD=''
MKINSTALLDIRS=''
MSGFMT=''
MSGMERGE=''
NO_PERL5='false'
OBJEXT=''
PACKAGE='R'
PACKAGE_BUGREPORT='r-bugs@R-project.org'
PACKAGE_NAME='R'
PACKAGE_STRING='R 2.3.1'
PACKAGE_TARNAME='R'
PACKAGE_VERSION='2.3.1'
PAGER='/usr/bin/less'
PAPERCONF=''
PATH_SEPARATOR=':'
PDFLATEX='false'
PDFTEX='false'
PERL='/usr/bin/perl'
POSUB=''
RANLIB=':'
READLINE_LIBS=''
RLAPACK_LDFLAGS=''
RMATH_HAVE_EXPM1=''
RMATH_HAVE_LOG1P=''
RMATH_HAVE_WORKING_LOG1P=''
RMATH_HAVE_WORKING_LOG=''
R_ARCH=''
R_BATCHSAVE=''
R_BROWSER='/usr/bin/firefox'
R_GZIPCMD='/bin/gzip'
R_JAVA_LD_LIBRARY_PATH=''
R_LD_LIBRARY_PATH=''
R_MODULES=''
R_OSTYPE='unix'
R_PAPERSIZE=''
R_PDFVIEWER='/usr/bin/open'
R_PLATFORM='i686-pc-linux-gnuoldld'
R_PRINTCMD=''
R_PROFILING=''
R_RD4DVI='ae'
R_RD4PDF='times,hyper'
R_UNZIPCMD='/usr/bin/unzip'
R_XTRA_CFLAGS=''
R_XTRA_CPPFLAGS=''
R_XTRA_CXXFLAGS=''
R_XTRA_FFLAGS=''
R_XTRA_LIBS=''
R_ZIPCMD='/usr/bin/zip'
SAFE_FFLAGS=''
SED='/bin/sed'
SET_MAKE=''
SHELL='/bin/sh'
SHLIB_CFLAGS=''
SHLIB_CXXFLAGS=''
SHLIB_CXXLD=''
SHLIB_CXXLDFLAGS=''
SHLIB_EXT=''
SHLIB_FCD=''
SHLIB_FCLD=''
SHLIB_FCLDFLAGS=''
SHLIB_FFLAGS=''
SHLIB_LD=''
SHLIB_LDFLAGS=''
SHLIB_LIBADD=''
STRIP=''
SUPPORT_MBCS=''
SUPPORT_UTF8=''
TAR='tar'
TCLTK_CPPFLAGS=''
TCLTK_LIBS=''
TCL_CONFIG=''
TEX='false'
TK_CONFIG=''
USE_EXPORTFILES_FALSE=''
USE_EXPORTFILES_TRUE=''
USE_EXTERNAL_BLAS_FALSE=''
USE_EXTERNAL_BLAS_TRUE=''
USE_EXTERNAL_LAPACK_FALSE=''
USE_EXTERNAL_LAPACK_TRUE=''
USE_INCLUDED_LIBINTL=''
USE_LIBTOOL_FALSE=''
USE_LIBTOOL_TRUE='#'
USE_MMAP_ZLIB_FALSE=''
USE_MMAP_ZLIB_TRUE=''
USE_NLS=''
USE_NLS_FALSE=''
USE_NLS_TRUE=''
USE_RECOMMENDED_PACKAGES_FALSE=''
USE_RECOMMENDED_PACKAGES_TRUE=''
USE_VECLIB_G95FIX_FALSE=''
USE_VECLIB_G95FIX_TRUE=''
VERSION='2.3.1'
WANT_R_FRAMEWORK_FALSE=''
WANT_R_FRAMEWORK_TRUE='#'
WANT_R_SHLIB_FALSE=''
WANT_R_SHLIB_TRUE='#'
XGETTEXT=''
XMKMF=''
XTRA_INTL_CPPFLAGS=''
X_CFLAGS=''
X_EXTRA_LIBS=''
X_LIBS=''
X_PRE_LIBS=''
YACC='yacc'
ac_ct_AR=''
ac_ct_CC=''
ac_ct_CXX=''
ac_ct_F77=''
ac_ct_FC=''
ac_ct_RANLIB=':'
ac_ct_STRIP=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnuoldld'
build_alias=''
build_cpu='i686'
build_os='linux-gnuoldld'
build_vendor='pc'
config_opts=''
datadir='${prefix}/share'
exec_prefix='NONE'
host='i686-pc-linux-gnuoldld'
host_alias=''
host_cpu='i686'
host_os='linux-gnuoldld'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/${LIBnn}'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
r_arch=''
rdocdir='${rhome}/doc'
rincludedir='${rhome}/include'
rsharedir='${rhome}/share'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
shlibpath_var=''
sysconfdir='${prefix}/etc'
target_alias=''
use_aqua=''
use_tcltk=''

## ------------- ##
## Output files. ##
## ------------- ##

r_cc_lo_rules_frag=''
r_cc_rules_frag=''
r_cxx_rules_frag=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "R"
#define PACKAGE_BUGREPORT "r-bugs@R-project.org"
#define PACKAGE_NAME "R"
#define PACKAGE_STRING "R 2.3.1"
#define PACKAGE_TARNAME "R"
#define PACKAGE_VERSION "2.3.1"
#define R_ARCH ""
#define R_CPU "i686"
#define R_OS "linux-gnuoldld"
#define R_PLATFORM "i686-pc-linux-gnuoldld"
#define R_VENDOR "pc"
#define Unix 1
#define VERSION "2.3.1"

configure: exit 1


---

### Post by neoeden on 2006-09-12
Have you installed build-essentials? You need it to build any software. After that, try running the configure again, and note which libraries it can't find. Search in synaptic for those and install the -dev packages. Ubuntu by default only installs the run-time libraries, not the ones you can use to compile with.

sudo apt-get install build-essential

---

