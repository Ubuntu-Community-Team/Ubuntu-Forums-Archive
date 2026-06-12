---
title: "Anybody successfully installed/uninstalled gforge package before?"
date: 2009-03-11
forum: General Help
---

### Post by oliu on 2009-03-11
Hi, 
   I am trying to install the gforge package on my 8.10 x86 desktop ubuntu installation. But I didn't get anywhere
   I did
     sudo apt-get install gforge
   Eventually I got an empty gforge directory under /var/www, I don't know how to start the gforge web browsing. So I gave up and decide to remove it from my machine. I did
     sudo apt-get remove gforge
   And then 
     sudo apt-get autoremove
   Then I got error back due to gforge-plugin-scmcvs dependency. Error is below:
-------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss-pgsql2 nscd libphp-snoopy cvs libipc-run-perl rcs
  gforge-shell-postgresql libio-pty-perl gforge-plugin-scmcvs
The following packages will be REMOVED:
  cvs gforge-plugin-scmcvs gforge-shell-postgresql libio-pty-perl
  libipc-run-perl libnss-pgsql2 libphp-snoopy nscd rcs
0 upgraded, 0 newly installed, 9 to remove and 25 not upgraded.
After this operation, 6152kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 153118 files and directories currently installed.)
Removing gforge-plugin-scmcvs ...
DBI connect('dbname=gforge','gforge',...) failed: FATAL:  Ident authentication failed for user "gforge" at /usr/lib/gforge/lib/include.pl line 37
Uncaught exception from user code:
        Error while connecting to database:  at /usr/lib/gforge/lib/include.pl line 39.
 at /usr/lib/gforge/lib/include.pl line 39
        main::db_connect called at /usr/lib/gforge/bin/unregister-plugin line 15
dpkg: error processing gforge-plugin-scmcvs (--remove):
 subprocess pre-removal script returned error exit status 255
Removing nscd ...
 * Stopping Name Service Cache Daemon nscd
   ...done.
dpkg: libphp-snoopy: dependency problems, but removing anyway as you request:
 gforge-plugin-scmcvs depends on libphp-snoopy.
Removing libphp-snoopy ...
dpkg: rcs: dependency problems, but removing anyway as you request:
 gforge-plugin-scmcvs depends on rcs; however:
  Package rcs is to be removed.
Removing rcs ...
dpkg: cvs: dependency problems, but removing anyway as you request:
 gforge-plugin-scmcvs depends on cvs.
Removing cvs ...
dpkg: gforge-shell-postgresql: dependency problems, but removing anyway as you request:
 gforge-plugin-scmcvs depends on gforge-shell-postgresql | gforge-shell; however:
  Package gforge-shell-postgresql is to be removed.
  Package gforge-shell is not installed.
  Package gforge-shell-postgresql which provides gforge-shell is to be removed.
 gforge-plugin-scmcvs depends on gforge-shell-postgresql | gforge-shell; however:
  Package gforge-shell-postgresql is to be removed.
  Package gforge-shell is not installed.
  Package gforge-shell-postgresql which provides gforge-shell is to be removed.
Removing gforge-shell-postgresql ...
Replacing config file /etc/nss-pgsql.conf with new version
dpkg: libipc-run-perl: dependency problems, but removing anyway as you request:
 gforge-plugin-scmcvs depends on libipc-run-perl; however:
  Package libipc-run-perl is to be removed.
Removing libipc-run-perl ...
Removing libio-pty-perl ...
Removing libnss-pgsql2 ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gforge-plugin-scmcvs
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------

Then I am never able to get rid of gforge anymore.

Thanks for your time and any help you may offer

---

### Post by oliu on 2009-03-11
I tried to install gforge again and just uninstall gforge-plugin-scmcvs and got following error:
-------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gforge-plugin-scmcvs
0 upgraded, 0 newly installed, 1 to remove and 25 not upgraded.
After this operation, 430kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 157139 files and directories currently installed.)
Removing gforge-plugin-scmcvs ...
DBI connect('dbname=gforge','gforge',...) failed: FATAL:  Ident authentication failed for user "gforge" at /usr/lib/gforge/lib/include.pl line 37
Uncaught exception from user code:
        Error while connecting to database:  at /usr/lib/gforge/lib/include.pl line 39.
 at /usr/lib/gforge/lib/include.pl line 39
        main::db_connect called at /usr/lib/gforge/bin/unregister-plugin line 15
dpkg: error processing gforge-plugin-scmcvs (--remove):
 subprocess pre-removal script returned error exit status 255
Errors were encountered while processing:
 gforge-plugin-scmcvs
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------

---

