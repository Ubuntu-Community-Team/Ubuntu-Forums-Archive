---
title: "(Perl) Trouble installing DBD::mysql from CPAN"
date: 2009-02-28
forum: General Help
---

### Post by CrazeDIzzleD on 2009-02-28
I'm trying to get Perl and all of its modules installed. I can't seem to install DBD::mysql. At first I had the missing C header mysql.h, but I installed the libmysqlclient15-dev (or something like that) package and that was fixed. But now, using the CPAN shell, I get this:

```
virtual@virtual-desktop:~$ sudo perl -MCPAN -e shell
Terminal does not support AddHistory.

cpan shell -- CPAN exploration and modules installation (v1.7602)
ReadLine support available (try 'install Bundle::CPAN')

cpan> install DBD::mysql
CPAN: Storable loaded ok
Going to read /home/virtual/.cpan/Metadata
  Database was generated on Fri, 27 Feb 2009 19:26:51 GMT
Running install for module DBD::mysql
Running make for C/CA/CAPTTOFU/DBD-mysql-4.010.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /home/virtual/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.010.tar.gz ok
Scanning cache /home/virtual/.cpan/build for sizes
DBD-mysql-4.010/
DBD-mysql-4.010/ChangeLog
DBD-mysql-4.010/constants.h
DBD-mysql-4.010/dbdimp.c
DBD-mysql-4.010/dbdimp.h
DBD-mysql-4.010/eg/
DBD-mysql-4.010/eg/._bug14979.pl
DBD-mysql-4.010/eg/bug14979.pl
DBD-mysql-4.010/eg/._bug21028.pl
DBD-mysql-4.010/eg/bug21028.pl
DBD-mysql-4.010/eg/bug30033.pl
DBD-mysql-4.010/eg/bug30033pg.pl
DBD-mysql-4.010/eg/decimal_test.pl
DBD-mysql-4.010/eg/issue21946.pl
DBD-mysql-4.010/eg/prepare_memory_usage.pl
DBD-mysql-4.010/eg/proc_example1.pl
DBD-mysql-4.010/eg/proc_example2.pl
DBD-mysql-4.010/eg/proc_example2a.pl
DBD-mysql-4.010/eg/proc_example2b.pl
DBD-mysql-4.010/eg/proc_example3.pl
DBD-mysql-4.010/eg/proc_example4.pl
DBD-mysql-4.010/INSTALL.html
DBD-mysql-4.010/lib/
DBD-mysql-4.010/lib/Bundle/
DBD-mysql-4.010/lib/Bundle/DBD/
DBD-mysql-4.010/lib/Bundle/DBD/mysql.pm
DBD-mysql-4.010/lib/DBD/
DBD-mysql-4.010/lib/DBD/mysql/
DBD-mysql-4.010/lib/DBD/mysql/GetInfo.pm
DBD-mysql-4.010/lib/DBD/mysql/INSTALL.pod
DBD-mysql-4.010/lib/DBD/mysql.pm
DBD-mysql-4.010/Makefile.PL
DBD-mysql-4.010/Makefile.PL.embedded
DBD-mysql-4.010/MANIFEST
DBD-mysql-4.010/MANIFEST.SKIP
DBD-mysql-4.010/META.yml
DBD-mysql-4.010/myld
DBD-mysql-4.010/mysql.xs
DBD-mysql-4.010/README
DBD-mysql-4.010/t/
DBD-mysql-4.010/t/00base.t
DBD-mysql-4.010/t/10connect.t
DBD-mysql-4.010/t/20createdrop.t
DBD-mysql-4.010/t/25lockunlock.t
DBD-mysql-4.010/t/29warnings.t
DBD-mysql-4.010/t/30insertfetch.t
DBD-mysql-4.010/t/31insertid.t
DBD-mysql-4.010/t/32insert_error.t
DBD-mysql-4.010/t/35limit.t
DBD-mysql-4.010/t/35prepare.t
DBD-mysql-4.010/t/40bindparam.t
DBD-mysql-4.010/t/40bindparam2.t
DBD-mysql-4.010/t/40blobs.t
DBD-mysql-4.010/t/40catalog.t
DBD-mysql-4.010/t/40keyinfo.t
DBD-mysql-4.010/t/40listfields.t
DBD-mysql-4.010/t/40nulls.t
DBD-mysql-4.010/t/40numrows.t
DBD-mysql-4.010/t/40server_prepare.t
DBD-mysql-4.010/t/40server_prepare_error.t
DBD-mysql-4.010/t/40types.t
DBD-mysql-4.010/t/41bindparam.t
DBD-mysql-4.010/t/41blobs_prepare.t
DBD-mysql-4.010/t/42bindparam.t
DBD-mysql-4.010/t/50chopblanks.t
DBD-mysql-4.010/t/50commit.t
DBD-mysql-4.010/t/55utf8.t
DBD-mysql-4.010/t/60leaks.t
DBD-mysql-4.010/t/65types.t
DBD-mysql-4.010/t/70takeimp.t
DBD-mysql-4.010/t/71impdata.t
DBD-mysql-4.010/t/75supported_sql.t
DBD-mysql-4.010/t/76multi_statement.t
DBD-mysql-4.010/t/80procs.t
DBD-mysql-4.010/t/lib.pl
DBD-mysql-4.010/t/mysql.dbtest
DBD-mysql-4.010/t/mysql.mtest
DBD-mysql-4.010/TODO
Removing previously used /home/virtual/.cpan/build/DBD-mysql-4.010

  CPAN.pm: Going to build C/CA/CAPTTOFU/DBD-mysql-4.010.tar.gz



PLEASE NOTE:

For 'make test' to run properly, you must ensure that the 
database user 'root' can connect to your MySQL server 
and has the proper privileges that these tests require such 
as 'drop table', 'create table', 'drop procedure', 'create procedure'
as well as others. 

mysql> grant all privileges on test.* to 'root'@'localhost' identified by 's3kr1t';

You can also optionally set the user to run 'make test' with:

perl Makefile.pl --testuser=username

I will use the following settings for compiling and testing:

  cflags        (mysql_config) = -I/usr/include/mysql -DBIG_JOINS=1 -fPIC
  embedded      (mysql_config) = 
  libs          (mysql_config) = -Wl,-Bsymbolic-functions -L/usr/lib/mysql -lmysqlclient
  mysql_config  (guessed     ) = mysql_config
  nocatchstderr (default     ) = 0
  nofoundrows   (default     ) = 0
  ssl           (guessed     ) = 0
  testdb        (default     ) = test
  testhost      (default     ) = 
  testpassword  (default     ) = 
  testsocket    (default     ) = 
Use of uninitialized value in printf at Makefile.PL line 175, <PIPE> line 93.
  testuser      (            ) = root

To change these settings, see 'perl Makefile.PL --help' and
'perldoc INSTALL'.

Argument "6.30_01" isn't numeric in numeric ge (>=) at Makefile.PL line 343, <PIPE> line 93.
Checking if your kit is complete...
Looks good
Unrecognized argument in LIBS ignored: '-Wl,-Bsymbolic-functions'
Using DBI 1.601 (for perl 5.008008 on x86_64-linux-gnu-thread-multi) installed in /usr/lib/perl5/auto/DBI/
Writing Makefile for DBD::mysql
cp lib/DBD/mysql.pm blib/lib/DBD/mysql.pm
cp lib/DBD/mysql/GetInfo.pm blib/lib/DBD/mysql/GetInfo.pm
cp lib/DBD/mysql/INSTALL.pod blib/lib/DBD/mysql/INSTALL.pod
cp lib/Bundle/DBD/mysql.pm blib/lib/Bundle/DBD/mysql.pm
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"4.010\" -DXS_VERSION=\"4.010\" -fPIC "-I/usr/lib/perl/5.8/CORE"   dbdimp.c
dbdimp.c: In function ‘alloc_param’:
dbdimp.c:112: warning: comparison is always false due to limited range of data type
dbdimp.c: In function ‘alloc_bind’:
dbdimp.c:130: warning: comparison is always false due to limited range of data type
dbdimp.c: In function ‘alloc_fbind’:
dbdimp.c:146: warning: comparison is always false due to limited range of data type
dbdimp.c: In function ‘alloc_fbuffer’:
dbdimp.c:161: warning: comparison is always false due to limited range of data type
/usr/bin/perl -p -e "s/~DRIVER~/mysql/g" /usr/lib/perl5/auto/DBI/Driver.xst > mysql.xsi
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap  mysql.xs > mysql.xsc && mv mysql.xsc mysql.c
Warning: duplicate function definition 'do' detected in mysql.xs, line 225
Warning: duplicate function definition 'rows' detected in mysql.xs, line 650
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"4.010\" -DXS_VERSION=\"4.010\" -fPIC "-I/usr/lib/perl/5.8/CORE"   mysql.c
mysql.xs: In function ‘XS_DBD__mysql__db_do’:
mysql.xs:330: warning: comparison is always false due to limited range of data type
mysql.xs:331: warning: comparison is always false due to limited range of data type
Running Mkbootstrap for DBD::mysql ()
chmod 644 mysql.bs
rm -f blib/arch/auto/DBD/mysql/mysql.so
/usr/bin/perl myld cc  -shared -L/usr/local/lib dbdimp.o mysql.o  -o blib/arch/auto/DBD/mysql/mysql.so 	\
	   -L/usr/lib/mysql -lmysqlclient  	\
	  
chmod 755 blib/arch/auto/DBD/mysql/mysql.so
cp mysql.bs blib/arch/auto/DBD/mysql/mysql.bs
chmod 644 blib/arch/auto/DBD/mysql/mysql.bs
Manifying blib/man3/DBD::mysql.3pm
Manifying blib/man3/DBD::mysql::INSTALL.3pm
Manifying blib/man3/Bundle::DBD::mysql.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00base....................ok                                               
t/10connect.................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO) Can't continue test
t/20createdrop..............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/25lockunlock..............skipped
        all skipped: Can't connect to database ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/29warnings................skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/29warnings.t line 15
t/30insertfetch.............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/31insertid................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/32insert_error............skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/32insert_error.t line 17
t/35limit...................skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/35limit.t line 18
t/35prepare.................skipped
        all skipped: Can't connect to database ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40bindparam...............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40bindparam2..............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40blobs...................Can't call method "get_info" on an undefined value at t/40blobs.t line 37.
t/40blobs...................dubious                                          
	Test returned status 255 (wstat 65280, 0xff00)
t/40catalog.................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40keyinfo.................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40listfields..............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40nulls...................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40numrows.................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/40server_prepare..........skipped
        all skipped: ERROR: DBI connect('test;mysql_server_prepare=1','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/40server_prepare.t line 16
t/40server_prepare_error....skipped
        all skipped: ERROR: DBI connect('test;mysql_server_prepare=1','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/40server_prepare_error.t line 18
t/40types...................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/41bindparam...............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/41blobs_prepare...........skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/42bindparam...............skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/42bindparam.t line 13
t/50chopblanks..............skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/50commit..................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/55utf8....................skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/55utf8.t line 18
t/60leaks...................skipped
        all skipped: Skip $ENV{SLOW_TESTS} is not set
t/65types...................skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/65types.t line 13
t/70takeimp.................skipped
        all skipped: Can't connect to database ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/70takeimp.t line 27
t/71impdata.................DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/71impdata.t line 14
skipped
        all skipped: Can't obtain driver handle. Can't continue test
t/75supported_sql...........skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
t/76multi_statement.........skipped
        all skipped: ERROR: DBI connect('test','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at t/76multi_statement.t line 15
t/80procs...................skipped
        all skipped: ERROR: Access denied for user 'root'@'localhost' (using password: NO). Can't continue test
Failed Test Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/40blobs.t  255 65280    ??   ??       %  ??
32 tests skipped.
Failed 1/34 test scripts, 97.06% okay. 0/6 subtests failed, 100.00% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

cpan>
```

I have made sure that the user root exists with no password, and that the database test exists. I have tested the connection with said credentials using PHP and it works fine, so why can't Perl connect?

Thanks.

---

