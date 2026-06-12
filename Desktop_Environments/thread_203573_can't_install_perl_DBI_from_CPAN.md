---
title: "can't install perl DBI from CPAN"
date: 2006-06-25
forum: Desktop Environments
---

### Post by bapple03 on 2006-06-25
I am trying to run the following:

```
sudo cpan -i DBI
```

I have installed several other modules from cpan, so as far as I know I have cpan configured and working properly. 

My error follows:

```


  CPAN.pm: Going to build T/TI/TIMB/DBI-1.51.tar.gz


*** You are using a perl configured with threading enabled.
*** You should be aware that using multiple threads is
*** not recommended for production environments.

*** Note:
    The optional PlRPC-modules (RPC::PlServer etc) are not installed.
    If you want to use the DBD::Proxy driver and DBI::ProxyServer
    modules, then you'll need to install the RPC::PlServer, RPC::PlClient,
    Storable and Net::Daemon modules. The CPAN Bundle::DBI may help you.
    You can install them any time after installing the DBI.
    You do *not* need these modules for typical DBI usage.

Optional modules are available from any CPAN mirror, in particular
    http://search.cpan.org/
    http://www.perl.com/CPAN/modules/by-module
    http://www.perl.org/CPAN/modules/by-module
    ftp://ftp.funet.fi/pub/languages/perl/CPAN/modules/by-module

Your perl was compiled with gcc (version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)), okay.
Creating DBI::PurePerl    test variant: t/zvpp_01basics.t
Creating DBI::PurePerl    .... (removed lines here for clarity)
Creating DBI::PurePerl    test variant: t/zvpp_80proxy.t
Checking if your kit is complete...
Looks good

    I see you're using perl 5.008007 on i486-linux-gnu-thread-multi, okay.
    Remember to actually *read* the README file!
    Use  'make' to build the software (dmake or nmake on Windows).
    Then 'make test' to execute self tests.
    Then 'make install' to install the DBI and then delete this working
    directory before unpacking and building any DBD::* drivers.

Writing Makefile for DBI
/usr/bin/perl "-MExtUtils::Command" -e mkpath blib/lib/DBI
rm -f blib/lib/DBI/Changes.pm
cp Changes blib/lib/DBI/Changes.pm
/usr/bin/perl "-MExtUtils::Command" -e mkpath blib/lib/DBI
rm -f blib/lib/DBI/Roadmap.pm
cp Roadmap.pod blib/lib/DBI/Roadmap.pm
cp ... (removed lines here for clarity)
cp lib/DBI/ProfileData.pm blib/lib/DBI/ProfileData.pm
/usr/bin/perl -p -e "s/~DRIVER~/Perl/g" ./Driver.xst > Perl.xsi
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  Perl.xs > Perl.xsc && mv Perl.xsc Perl.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"1.51\" -DXS_VERSION=\"1.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -W -Wall -Wpointer-arith -Wbad-function-cast -Wno-comment -Wno-sign-compare -Wno-cast-qual -Wmissing-noreturn -Wno-unused-parameter Perl.c
In file included from DBIXS.h:19,
                 from Perl.xs:6:
**/usr/lib/perl/5.8/CORE/perl.h:382:24: error: sys/types.h: No such file or directory**
/usr/lib/perl/5.8/CORE/perl.h:413:19: error: ctype.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:425:23: error: locale.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:442:20: error: setjmp.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:448:26: error: sys/param.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:453:23: error: stdlib.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:458:23: error: unistd.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:731:23: error: string.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:880:27: error: netinet/in.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:884:26: error: arpa/inet.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:894:25: error: sys/stat.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:916:21: error: time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:923:25: error: sys/time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:930:27: error: sys/times.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:937:19: error: errno.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:952:25: error: sys/socket.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:979:21: error: netdb.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1081:24: error: sys/ioctl.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1110:23: error: dirent.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:11,
                 from /usr/lib/perl/5.8/CORE/perl.h:1446,
                 from DBIXS.h:19,
                 from Perl.xs:6:
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2056,
                 from DBIXS.h:19,
                 from Perl.xs:6:
/usr/lib/perl/5.8/CORE/handy.h:121:25: error: inttypes.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2220,
                 from DBIXS.h:19,
                 from Perl.xs:6:
/usr/lib/perl/5.8/CORE/unixish.h:106:21: error: signal.h: No such file or directory
In file included from DBIXS.h:19,
                 from Perl.xs:6:

```

I think perhaps something is not right with gcc.  Perhaps I'm missing a package?  Any help would be appreciated.

---

### Post by bapple03 on 2006-06-25
I will admit that I am no C or compiler expert... more of a perl rat... but I think I've solved this by running the following

sudo apt-get install libc6-dev

I found this in a post outside of Ubuntu.  I am going to mark this thread as solved.  I hope this helps someone in the future

---

### Post by cbschuld on 2006-07-28
Adding the libc6-dev package definitely solves this problem.  Thanks!

---

### Post by suggsjc on 2006-08-07
I am having the same problem, but a different error.  FYI, I installed libc6-dev, but that didn't help either.

Below is the log from my attemp...sorry for the long snippet

```
admin@srv:~/DBI-1.51$ sudo cpan -i DBI
CPAN: Storable loaded ok
Going to read /home/admin/.cpan/Metadata
  Database was generated on Mon, 07 Aug 2006 10:28:55 GMT
Running install for module DBI
Running make for T/TI/TIMB/DBI-1.51.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /home/admin/.cpan/sources/authors/id/T/TI/TIMB/DBI-1.51.tar.gz ok
Scanning cache /home/admin/.cpan/build for sizes
DBI-1.51/
DBI-1.51/Changes
DBI-1.51/dbd_xsh.h
DBI-1.51/DBI.pm
DBI-1.51/DBI.xs
DBI-1.51/dbi_sql.h
DBI-1.51/dbipport.h
DBI-1.51/dbiprof.PL
DBI-1.51/dbiproxy.PL
DBI-1.51/dbivport.h
DBI-1.51/DBIXS.h
DBI-1.51/Driver.xst
DBI-1.51/Driver_xst.h
DBI-1.51/ex/
DBI-1.51/ex/perl_dbi_nulls_test.pl
DBI-1.51/lib/
DBI-1.51/lib/Bundle/
DBI-1.51/lib/Bundle/DBI.pm
DBI-1.51/lib/DBD/
DBI-1.51/lib/DBD/DBM.pm
DBI-1.51/lib/DBD/ExampleP.pm
DBI-1.51/lib/DBD/File.pm
DBI-1.51/lib/DBD/NullP.pm
DBI-1.51/lib/DBD/Proxy.pm
DBI-1.51/lib/DBD/Sponge.pm
DBI-1.51/lib/DBI/
DBI-1.51/lib/DBI/Const/
DBI-1.51/lib/DBI/Const/GetInfo/
DBI-1.51/lib/DBI/Const/GetInfo/ANSI.pm
DBI-1.51/lib/DBI/Const/GetInfo/ODBC.pm
DBI-1.51/lib/DBI/Const/GetInfoReturn.pm
DBI-1.51/lib/DBI/Const/GetInfoType.pm
DBI-1.51/lib/DBI/DBD/
DBI-1.51/lib/DBI/DBD/Metadata.pm
DBI-1.51/lib/DBI/DBD.pm
DBI-1.51/lib/DBI/FAQ.pm
DBI-1.51/lib/DBI/Profile.pm
DBI-1.51/lib/DBI/ProfileData.pm
DBI-1.51/lib/DBI/ProfileDumper/
DBI-1.51/lib/DBI/ProfileDumper/Apache.pm
DBI-1.51/lib/DBI/ProfileDumper.pm
DBI-1.51/lib/DBI/ProxyServer.pm
DBI-1.51/lib/DBI/PurePerl.pm
DBI-1.51/lib/DBI/SQL/
DBI-1.51/lib/DBI/SQL/Nano.pm
DBI-1.51/lib/DBI/W32ODBC.pm
DBI-1.51/lib/Win32/
DBI-1.51/lib/Win32/DBIODBC.pm
DBI-1.51/Makefile.PL
DBI-1.51/MANIFEST
DBI-1.51/META.yml
DBI-1.51/Perl.xs
DBI-1.51/README
DBI-1.51/Roadmap.pod
DBI-1.51/t/
DBI-1.51/t/01basics.t
DBI-1.51/t/02dbidrv.t
DBI-1.51/t/03handle.t
DBI-1.51/t/04mods.t
DBI-1.51/t/05thrclone.t
DBI-1.51/t/06attrs.t
DBI-1.51/t/07kids.t
DBI-1.51/t/08keeperr.t
DBI-1.51/t/09trace.t
DBI-1.51/t/10examp.t
DBI-1.51/t/11fetch.t
DBI-1.51/t/14utf8.t
DBI-1.51/t/15array.t
DBI-1.51/t/20meta.t
DBI-1.51/t/30subclass.t
DBI-1.51/t/40profile.t
DBI-1.51/t/41prof_dump.t
DBI-1.51/t/42prof_data.t
DBI-1.51/t/43profenv.t
DBI-1.51/t/50dbm.t
DBI-1.51/t/60preparse.t
DBI-1.51/t/70callbacks.t
DBI-1.51/t/72childhandles.t
DBI-1.51/t/80proxy.t
DBI-1.51/t/pod.t
DBI-1.51/test.pl
DBI-1.51/ToDo
DBI-1.51/typemap
Removing previously used /home/admin/.cpan/build/DBI-1.51

  CPAN.pm: Going to build T/TI/TIMB/DBI-1.51.tar.gz


*** You are using a perl configured with threading enabled.
*** You should be aware that using multiple threads is
*** not recommended for production environments.

Your perl was compiled with gcc (version 4.0.3 20051204 (prerelease) (Ubuntu 4.0.2-5ubuntu2)), okay.
Creating DBI::PurePerl    test variant: t/zvpp_01basics.t 
Creating DBI::PurePerl    test variant: t/zvpp_02dbidrv.t 
Creating DBI::PurePerl    test variant: t/zvpp_03handle.t 
Creating DBI::PurePerl    test variant: t/zvpp_04mods.t 
Creating DBI::PurePerl    test variant: t/zvpp_05thrclone.t (use threads)
Creating DBI::PurePerl    test variant: t/zvpp_06attrs.t 
Creating DBI::PurePerl    test variant: t/zvpp_07kids.t 
Creating DBI::PurePerl    test variant: t/zvpp_08keeperr.t 
Creating DBI::PurePerl    test variant: t/zvpp_09trace.t 
Creating DBI::PurePerl    test variant: t/zvpp_10examp.t 
Creating DBI::PurePerl    test variant: t/zvpp_11fetch.t 
Creating DBI::PurePerl    test variant: t/zvpp_14utf8.t 
Creating DBI::PurePerl    test variant: t/zvpp_15array.t 
Creating DBI::PurePerl    test variant: t/zvpp_20meta.t 
Creating DBI::PurePerl    test variant: t/zvpp_30subclass.t 
Creating DBI::PurePerl    test variant: t/zvpp_40profile.t 
Creating DBI::PurePerl    test variant: t/zvpp_41prof_dump.t 
Creating DBI::PurePerl    test variant: t/zvpp_42prof_data.t 
Creating DBI::PurePerl    test variant: t/zvpp_43profenv.t 
Creating DBI::PurePerl    test variant: t/zvpp_50dbm.t 
Creating DBI::PurePerl    test variant: t/zvpp_60preparse.t 
Creating DBI::PurePerl    test variant: t/zvpp_70callbacks.t 
Creating DBI::PurePerl    test variant: t/zvpp_72childhandles.t 
Creating DBI::PurePerl    test variant: t/zvpp_80proxy.t 
Checking if your kit is complete...
Looks good

    I see you're using perl 5.008007 on i486-linux-gnu-thread-multi, okay.
    Remember to actually *read* the README file!
    Use  'make' to build the software (dmake or nmake on Windows).
    Then 'make test' to execute self tests.
    Then 'make install' to install the DBI and then delete this working
    directory before unpacking and building any DBD::* drivers.

Writing Makefile for DBI
/usr/bin/perl "-MExtUtils::Command" -e mkpath blib/lib/DBI
rm -f blib/lib/DBI/Changes.pm
cp Changes blib/lib/DBI/Changes.pm
/usr/bin/perl "-MExtUtils::Command" -e mkpath blib/lib/DBI
rm -f blib/lib/DBI/Roadmap.pm
cp Roadmap.pod blib/lib/DBI/Roadmap.pm
cp dbd_xsh.h blib/arch/auto/DBI/dbd_xsh.h
cp dbivport.h blib/arch/auto/DBI/dbivport.h
cp lib/DBI/FAQ.pm blib/lib/DBI/FAQ.pm
cp Driver_xst.h blib/arch/auto/DBI/Driver_xst.h
cp lib/DBD/Proxy.pm blib/lib/DBD/Proxy.pm
cp lib/DBI/SQL/Nano.pm blib/lib/DBI/SQL/Nano.pm
cp lib/DBI/Const/GetInfo/ANSI.pm blib/lib/DBI/Const/GetInfo/ANSI.pm
cp lib/DBD/DBM.pm blib/lib/DBD/DBM.pm
cp DBI.pm blib/lib/DBI.pm
cp lib/DBI/Const/GetInfoReturn.pm blib/lib/DBI/Const/GetInfoReturn.pm
cp DBIXS.h blib/arch/auto/DBI/DBIXS.h
cp lib/DBD/Sponge.pm blib/lib/DBD/Sponge.pm
cp Roadmap.pod blib/lib/Roadmap.pod
cp lib/DBI/Const/GetInfoType.pm blib/lib/DBI/Const/GetInfoType.pm
cp lib/DBI/W32ODBC.pm blib/lib/DBI/W32ODBC.pm
cp lib/DBI/DBD/Metadata.pm blib/lib/DBI/DBD/Metadata.pm
cp lib/DBI/Const/GetInfo/ODBC.pm blib/lib/DBI/Const/GetInfo/ODBC.pm
cp lib/DBI/ProfileDumper/Apache.pm blib/lib/DBI/ProfileDumper/Apache.pm
cp lib/Bundle/DBI.pm blib/lib/Bundle/DBI.pm
cp lib/DBI/Profile.pm blib/lib/DBI/Profile.pm
cp lib/DBI/ProfileDumper.pm blib/lib/DBI/ProfileDumper.pm
cp lib/DBD/File.pm blib/lib/DBD/File.pm
cp Driver.xst blib/arch/auto/DBI/Driver.xst
cp lib/DBI/ProxyServer.pm blib/lib/DBI/ProxyServer.pm
cp dbipport.h blib/arch/auto/DBI/dbipport.h
cp lib/DBD/NullP.pm blib/lib/DBD/NullP.pm
cp lib/DBI/DBD.pm blib/lib/DBI/DBD.pm
cp lib/Win32/DBIODBC.pm blib/lib/Win32/DBIODBC.pm
cp lib/DBI/PurePerl.pm blib/lib/DBI/PurePerl.pm
cp lib/DBD/ExampleP.pm blib/lib/DBD/ExampleP.pm
cp dbi_sql.h blib/arch/auto/DBI/dbi_sql.h
cp lib/DBI/ProfileData.pm blib/lib/DBI/ProfileData.pm
/usr/bin/perl -p -e "s/~DRIVER~/Perl/g" ./Driver.xst > Perl.xsi
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  Perl.xs > Perl.xsc && mv Perl.xsc Perl.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"1.51\" -DXS_VERSION=\"1.51\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -W -Wall -Wpointer-arith -Wbad-function-cast -Wno-comment -Wno-sign-compare -Wno-cast-qual -Wmissing-noreturn -Wno-unused-parameter Perl.c
/bin/sh: cc: command not found
make: *** [Perl.o] Error 127
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
```

---

### Post by ctcmbz on 2007-03-23
definitely solved my problem, thanks for the original post and solution!

---

