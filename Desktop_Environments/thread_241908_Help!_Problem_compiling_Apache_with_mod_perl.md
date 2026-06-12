---
title: "Help! Problem compiling Apache with mod_perl"
date: 2006-08-22
forum: Desktop Environments
---

### Post by ChantCd_com on 2006-08-22
I'm trying to compile Apache with mod_perl, and I'm getting this error. I'm on a Ubuntu 6.06.1 (LTS) Server box -- it has a real minimal install.

What am I missing here?
There is a TON of mesages like this, but they all seem to reference the same functions.

This is perl, v5.8.7 built for i486-linux-gnu-thread-multi
My perl5: (revision 5 version 8 subversion 7) 


Table.c:(.text+0x21a4): undefined reference to `Perl_Gthr_key_ptr'
Table.c:(.text+0x21b6): undefined reference to `Perl_Top_ptr'
Table.c:(.text+0x21ce): undefined reference to `Perl_Gthr_key_ptr'
Table.c:(.text+0x21e0): undefined reference to `Perl_Tcurpad_ptr'
Table.c:(.text+0x21ee): undefined reference to `Perl_Gthr_key_ptr'
Table.c:(.text+0x2200): undefined reference to `Perl_Top_ptr'
Table.c:(.text+0x221c): undefined reference to `Perl_Gthr_key_ptr'

---

### Post by ChantCd_com on 2006-08-25
I am still having a problem compiling Apache on Ubuntu Server 6.06 LTS.
I can solve THIS problem at least by installing Perl 5.8.8 from source -- but I don't know which directories to use so that it will completely overwrite the old Perl. Do I have to install or move all my existing Perl modules after the upgrade to 5.8.8?

I heard about a utility called CPAN.pm which catalogs all your modules, and downloads them again for you easily after an upgrade. Does that mean there's no way to install a new version of Perl and not have to install everything else over again?

I'm thinking that if I knew enough about Perl installation, I'd be able to tell it to use the right directories, and it would overwrite the old one and there'd be no problems. I mean, I'm only upgrading from 5.8.7 to 5.8.8 -- it can't be that big of a change.

But it's enough of a change to fix my problem (see end of post). I think it's more because I'm compiling it myself, rather than something in the Perl executable itself.

Any ideas? Anyone else had this same problem? 

Thanks,

Matthew
matthew at tanbooks dot com

===============================================================
About my Perl version (it came pre-installed with Ubuntu):

(Short version -v)
This is perl, v5.8.7 built for i486-linux-gnu-thread-multi

(Long version -V)
Summary of my perl5 (revision 5 version 8 subversion 7) configuration:
  Platform:
    osname=linux, osvers=2.6.10, archname=i486-linux-gnu-thread-multi
    uname='linux rothera 2.6.10 #1 smp fri may 13 09:24:22 utc 2005 i686 gnulinux '
    config_args='-Dusethreads -Duselargefiles -Dccflags=-DDEBIAN -Dcccdlflags=-fPIC -Darchname=i486-linux-gnu -Dprefix=/usr -Dprivlib=/usr/share/perl/5.8 -Darchlib=/usr/lib/perl/5.8 -Dvendorprefix=/usr -Dvendorlib=/usr/share/perl5 -Dvendorarch=/usr/lib/perl5 -Dsiteprefix=/usr/local -Dsitelib=/usr/local/share/perl/5.8.7 -Dsitearch=/usr/local/lib/perl/5.8.7 -Dman1dir=/usr/share/man/man1 -Dman3dir=/usr/share/man/man3 -Dsiteman1dir=/usr/local/man/man1 -Dsiteman3dir=/usr/local/man/man3 -Dman1ext=1 -Dman3ext=3perl -Dpager=/usr/bin/sensible-pager -Uafs -Ud_csh -Uusesfio -Uusenm -Duseshrplib -Dlibperl=libperl.so.5.8.7 -Dd_dosuid -des'
    hint=recommended, useposix=true, d_sigaction=define
    usethreads=define use5005threads=undef useithreads=define usemultiplicity=define
    useperlio=define d_sfio=undef uselargefiles=define usesocks=undef
    use64bitint=undef use64bitall=undef uselongdouble=undef
    usemymalloc=n, bincompat5005=undef
  Compiler:
    cc='cc', ccflags ='-D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64',
    optimize='-O2',
    cppflags='-D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include'
    ccversion='', gccversion='4.0.3 20051204 (prerelease) (Ubuntu 4.0.2-5ubuntu2)', gccosandvers=''
    intsize=4, longsize=4, ptrsize=4, doublesize=8, byteorder=1234
    d_longlong=define, longlongsize=8, d_longdbl=define, longdblsize=12
    ivtype='long', ivsize=4, nvtype='double', nvsize=8, Off_t='off_t', lseeksize=8
    alignbytes=4, prototype=define
  Linker and Libraries:
    ld='cc', ldflags =' -L/usr/local/lib'
    libpth=/usr/local/lib /lib /usr/lib
    libs=-lgdbm -lgdbm_compat -ldb -ldl -lm -lpthread -lc -lcrypt
    perllibs=-ldl -lm -lpthread -lc -lcrypt
    libc=/lib/libc-2.3.5.so, so=so, useshrplib=true, libperl=libperl.so.5.8.7
    gnulibc_version='2.3.5'
  Dynamic Linking:
    dlsrc=dl_dlopen.xs, dlext=so, d_dlsymun=undef, ccdlflags='-Wl,-E'
    cccdlflags='-fPIC', lddlflags='-shared -L/usr/local/lib'


Characteristics of this binary (from libperl):
  Compile-time options: MULTIPLICITY USE_ITHREADS USE_LARGE_FILES
                        PERL_IMPLICIT_CONTEXT
  Locally applied patches:
        SPRINTF0 - fixes for sprintf formatting issues - CVE-2005-3962
  Built under linux
  Compiled at Dec 16 2005 07:48:39
  @INC:
    /etc/perl
    /usr/local/lib/perl/5.8.7
    /usr/local/share/perl/5.8.7
    /usr/lib/perl5
    /usr/share/perl5
    /usr/lib/perl/5.8
    /usr/share/perl/5.8
    /usr/local/lib/site_perl
===============================================================

Here are 5% of the error messages I get (they mostly look like this):

:Table.c:(.text+0x3207): undefined reference to `Perl_Gthr_key_ptr'
:Table.c:(.text+0x3231): undefined reference to `Perl_newXS'
:Table.c:(.text+0x323d): undefined reference to `Perl_Gthr_key_ptr'
:Table.c:(.text+0x324f): undefined reference to `Perl_Tstack_base_ptr'
:Table.c:(.text+0x3263): undefined reference to `Perl_Gthr_key_ptr'
:Table.c:(.text+0x3275): undefined reference to `Perl_Isv_yes_ptr'
:Table.c:(.text+0x3283): undefined reference to `Perl_Gthr_key_ptr'
:Table.c:(.text+0x3295): undefined reference to `Perl_Tstack_sp_ptr'
:Table.c:(.text+0x32a3): undefined reference to `Perl_Gthr_key_ptr'
:Table.c:(.text+0x32b5): undefined reference to `Perl_Tstack_base_ptr'
...
Loader.c:(.text+0x39c): undefined reference to `Perl_mg_set'
:DynaLoader.c:(.text+0x3d9): undefined reference to `Perl_sv_newmortal'
:DynaLoader.c:(.text+0x3ed): undefined reference to `Perl_sv_2iv'
:DynaLoader.c:(.text+0x407): undefined reference to `Perl_croak'
/usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a(DynaLoader.o): In function `XS_DynaLoader_dl_find_symbol':DynaLoader.c:(.text+0x492): undefined reference to `Perl_sv_newmortal'
:DynaLoader.c:(.text+0x4b7): undefined reference to `Perl_sv_setiv'
:DynaLoader.c:(.text+0x4d6): undefined reference to `Perl_sv_2iv'
:DynaLoader.c:(.text+0x4f8): undefined reference to `Perl_sv_2pv_nolen'
:DynaLoader.c:(.text+0x53d): undefined reference to `Perl_croak'

---

