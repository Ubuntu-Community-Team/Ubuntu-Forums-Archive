---
title: "Random python crap"
date: 2006-02-16
forum: Desktop Environments
---

### Post by nigelenki on 2006-02-16
I noticed Ubuntu installs a lot of random Python packages i.e. bicyclerepair and such in the ubuntu-desktop package.  This should probably be relegated to ubuntu-python-dev or something, because there's definitely nothing using them, and the random python developer's packages and bindings are an invisible waste of space to the typical end user.

---

### Post by cwaldbieser on 2006-02-16
[QUOTE=nigelenki]I noticed Ubuntu installs a lot of random Python packages i.e. bicyclerepair and such in the ubuntu-desktop package.  This should probably be relegated to ubuntu-python-dev or something, because there's definitely nothing using them, and the random python developer's packages and bindings are an invisible waste of space to the typical end user.[/QUOTE]
How can you tell the packages aren't being used?

---

### Post by nigelenki on 2006-02-16
Well my first hint was that removing them removes either precisely ubuntu-desktop, or else other python bindings that no real application depends on.

My second was that bicyclerepair isn't a component of anything, it's a programmer tool, like gcc.

---

### Post by nigelenki on 2006-02-19
Try 'bicyclerepair' or 'mysql-common'

On Dapper, yanking 'mysql-common' removes:

 libmysqlclient12
 libmysqlquient15
 librdf0
 python-mysqldb
 python2.4-librdf
 python2.4-mysqldb
 ubuntu-desktop

Lo and behold, a bunch of libraries and python bindings, but no actual applications using them.

diveintopython pops out ubuntu-desktop only.  "Dive Into Python is a free Python tutorial, written by Mark Pilgrim."

Some others just ringing to ubuntu-desktop, most of which resolv to python2.4-*:

 gimp-python  (gimp has about 3 python plug-ins by default)
 python-adns
 python-clientcookie
 python-crypto
 python-dictclient
 python-egenix-mxdatetime
 python-egenix-mxproxy
 python-egenix-mxstack
 python-egenix-mxtexttools
 python-egenix-mxtools
 python-epydoc
 python-eunuchs
 python-examples (wtf?)
 python-gadfly
 python-gd
 python-gdbm
 python-geoip
 python-htmlgen
 python-htmltmpl
 python-id3lib
 python-imaging
 python-imaging-sane
 python-jabber
 python-kjbuckets
 python-ldap
 python-librdf
 python2.4-libxslt1
 python-mysqldb
 python-osd
 python-pam
 python-pexpect
 python-pgsql
 python2.4-pycurl
 python-pylibacl
 python-pyopenssl
 python-pyxattr
 python-reportlab
 python-simpletal
 python-soappy
 python-sqlite
 python-syck
 python-tk
 python-unit
 python-xmpp
 python-cddb

These seem to be there too, but just 'python' and not 'python2.4' at this point:
 python-gdchart
 python-genetic
 python-gnupginterface
 python-gst (python-gst0.10 is separate, for serpentine)
 python-netcdf
 python-newt
 python-parted
 python-pisock
 python-pqueue
 python-pyao
 python-pyogg
 python-pyvorbis
 python-stats

I have not checked what LIBRARIES these depend on.  I will install deborphan and start weeding through to get space usage checks later.

---

### Post by nigelenki on 2006-02-19
[QUOTE=nigelenki]I have not checked what LIBRARIES these depend on.  I will install deborphan and start weeding through to get space usage checks later.[/QUOTE]

Checking done.  I removed all the python stuff; here's what we got:

```
bluefox@icebox:~/misc/trebuchet-1.067$ sudo apt-get install ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  bicyclerepair diveintopython libadns1 libcurl3 libgd1-noxpm libgd2-noxpm
  libgdchart-gd1-noxpm libgeoip1 libgmp3c2 libid3-3.8.3c2a libmysqlclient15
  libnetcdf3 libpq4 libraptor1 librasqal0 librdf0 libsqlite0 libsqlite3-0
  python-adns python-cddb python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-eunuchs python-examples
  python-gadfly python-gd python-gdbm python-gdchart python-genetic
  python-geoip python-gnupginterface python-gst python-htmlgen python-htmltmpl
  python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt
  python-numeric python-pam python-parted python-pexpect python-pgsql
  python-pisock python-pqueue python-pyao python-pylibacl python-pyogg
  python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-unit python-xmpp python2.4-adns
  python2.4-clientcookie python2.4-crypto python2.4-dictclient
  python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxslt1
  python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql
  python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyxattr
  python2.4-reportlab python2.4-simpletal python2.4-soappy python2.4-sqlite
  python2.4-syck python2.4-tk python2.4-unit python2.4-xmpp
Suggested packages:
  vim-python idle pymacs libgd-tools geoip-bin netcdf-doc epydoc-doc
  python-imaging-doc python-egenix-mxdatetime python-numeric-tutorial
  python-reportlab-doc dictd python-ldap-doc mysql-server-4.1 mysql-server
  libcurl3-gnutls-dev pyopenssl-doc tix
Recommended packages:
  libadns1-bin raptor-utils redland-utils tetex-extra
  python2.4-reportlab-accel
The following NEW packages will be installed:
  bicyclerepair diveintopython libadns1 libcurl3 libgd1-noxpm libgd2-noxpm
  libgdchart-gd1-noxpm libgeoip1 libgmp3c2 libid3-3.8.3c2a libmysqlclient15
  libnetcdf3 libpq4 libraptor1 librasqal0 librdf0 libsqlite0 libsqlite3-0
  python-adns python-cddb python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-epydoc python-eunuchs python-examples
  python-gadfly python-gd python-gdbm python-gdchart python-genetic
  python-geoip python-gnupginterface python-gst python-htmlgen python-htmltmpl
  python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt
  python-numeric python-pam python-parted python-pexpect python-pgsql
  python-pisock python-pqueue python-pyao python-pylibacl python-pyogg
  python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-stats
  python-syck python-tk python-unit python-xmpp python2.4-adns
  python2.4-clientcookie python2.4-crypto python2.4-dictclient
  python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxslt1
  python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql
  python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyxattr
  python2.4-reportlab python2.4-simpletal python2.4-soappy python2.4-sqlite
  python2.4-syck python2.4-tk python2.4-unit python2.4-xmpp ubuntu-desktop
0 upgraded, 114 newly installed, 0 to remove and 0 not upgraded.
Need to get 1447kB/9741kB of archives.
After unpacking 41.8MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

So all in all 9.5MiB of packages to download, 41.8MiB to install.  Quite frankly that's a lot of junk, especially for slow DSL users (*I've seen 100k/s when your line is ugly*) or people in developing countries (*OSDL's One Laptop Per Child effort aims here*) that have only dial-up and 3-4 gig hard drives.  Besides, on my Athlon 64 Newcastle 1.8GHz in 64 bit mode with a SerialATA hard drive and 1 gig of RAM (half used):

```
bluefox@icebox:~/misc/trebuchet-1.067$ yes|sudo time apt-get install ubuntu-desktop
........
19.52user 9.96system 0:44.90elapsed 65%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (8major+855087minor)pagefaults 0swaps

```

This was done after an 'apt-get -d install', so all packages were downloaded.  19.52 user, 9.96 system, 45 seconds of realtime on my beefy system on AMD64 Ubuntu.  45 seconds of wasted time to install junk I don't need.

ubuntu-python-devel would be nice.

---

### Post by ow50 on 2006-02-19
ubuntu-desktop is a bloated and unecessary package. There's a lot more junk than just python stuff. If you're doing a fresh install and you're not a beginner, better install only ubuntu-base, and after that only the packages you need.

---

### Post by nigelenki on 2006-02-20
Really?  What other junk besides python stuff is there?  ubuntu-desktop comes with a lot of applications you may/may not need, but that's end-user-visible.  It's supposed to have openoffice.org and firefox and evolution and gaim, because people use those; on the other hand, there's a lot of python stuff people don't see (i.e. it's not in the menus) and won't use (unless they're python developers; but then ther's C, C++, objective-c, perl, PHP, tcl/tk, etc that we're not touching).

---

### Post by pulp on 2006-02-21
Well, I have to agree, that there is some other stuff besides these python packages, that shouldn't be installed by default with the ubuntu-**desktop** package like i.e. mutt or w3m and all that other things a point-and-click desktop user won't ever need.
At least there should be a discussion on how to differentiate the metapackages and maybe a way to select and deselect them on install.

There is a huge possibility, if i chose de-de and Germany for the localization and timezone stuff, that I'm in no need for all these east Asian ttf font packages.

---

