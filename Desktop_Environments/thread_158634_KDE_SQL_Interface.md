---
title: "KDE SQL Interface?"
date: 2006-04-11
forum: Desktop Environments
---

### Post by tagg3rx on 2006-04-11
Hi All - is there a GUI tool for managing your SQL databases?
Doing it from the command line is proving to be a daunting.

Thank you

---

### Post by gerbman on 2006-04-12
[QUOTE=tagg3rx]Hi All - is there a GUI tool for managing your SQL databases?
Doing it from the command line is proving to be a daunting.

Thank you[/QUOTE]Hi. If it's a MySQL DB you can use the [Administrator]("http://www.mysql.com/products/tools/administrator/") and the [Control Center]("http://sourceforge.net/project/showfiles.php?group_id=66393") - the former for admin stuff (user management, etc.) and the latter for maintaining the DB itself (table creation, executing queries, etc.). I like both of them.

---

### Post by tagg3rx on 2006-04-12
That looks exactly like what i'm looking for 

Oh goodie I get to compile it from source.

Thanks for the links.  If I need help on the ./configure make install I'll be posting...

Thanks!

---

### Post by tagg3rx on 2006-04-12
Avast I have once agian failed to configure said module.

```
checking for libglade-2.0
                        libxml-2.0 >= 2.6.2
                        gtkmm-2.4... Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found
configure: error: Library requirements (libglade-2.0
                        libxml-2.0 >= 2.6.2
                        gtkmm-2.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

```
penguin@95-ubuntu:~/mysql-administrator-1.1.6/mysql-administrator$ sudo apt-get install libglade-2.0
................
E: Couldn't find package libglade-2.0

```

AND my Sources.list for review
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
#deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

# Osmo Salomas CVS amule packages (packages, GPG key: 70188C3B)
deb [http://koti.mbnet.fi/~ots/ubuntu](http://koti.mbnet.fi/~ots/ubuntu) breezy/

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free


Your assistance is appriciated.
Thanks

---

### Post by hater2win on 2006-04-12
You can download the RPM and then convert it to a debian package with alien. If you download it and its called  administrator.rpm do:

```
sudo alien /path/to/administrator.rpm
sudo dpkg -i administrator.deb
```

you do the second line once the first finishes...

hope that helps!

EDIT: There is also the mysql-admin package in the repos (universe)
EDIT2: You may also want to use PHPMyAdmin, thats a great program for GUI MySQL editing. It runs off your server too, so if you need to edit databases remotely, you can still use it. (PHPMyAdmin is also in universe)

---

### Post by gerbman on 2006-04-12
```
checking for libglade-2.0
                        libxml-2.0 >= 2.6.2
                        gtkmm-2.4... Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found
configure: error: Library requirements (libglade-2.0
                        libxml-2.0 >= 2.6.2
                        gtkmm-2.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```I think the packages you want for those dependencies are the following:

libglade-2.0:  libglade2-0
libxml-2.0:  libxml2
gtkmm-2.4:  libgtkmm-2.4-1c2

I haven't tried it, so they might not be the right ones. You can always search for different ones by doing ```
apt-cache search <missing dependency>
```where <missing dependency> is the missing requirement reported. It works best to leave off version numbers and just include the main library name for what you're looking for...gets you the most results. For example, instead of searching for libxml-2.0 I just searched for libxml.

---

### Post by tagg3rx on 2006-04-12
Hurm Alien sounds awesome - I've had so manny failed compiles I'm beginning to loathe trying to do anything not in the repos (but hey that wouldent be any fun) 

Downloaded the adminconsole.deb file
Converted with alien 
Installed the .deb using dpkg
And all seemed to go well

but now when i try and run it I get the following

> penguin@95-ubuntu:~$ mysql-administrator
/usr/bin/mysql-administrator-bin: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory


mysql-admin is the standard bash interface and its making my brain hurt i dont even know how manny sql databases i have created or what users i set up on which and how many records are in each database etc....

I'll try the phpadmin next

Thanks for the help

---

### Post by der_joachim on 2006-04-13
OpenOffice 2 has a database frontend program called Base. Apparently, it even supports ODBC, although I have never succeeded in getting it to work with MSSQL.

---

### Post by thewump on 2008-04-14
I know this is an old thread, but for what it's worth, I'm finding mysqlcc really good.

I've been using Navicat for a couple of years ( windows before Linux ) and really like it, but issues with window decoration under compiz has just gotten too painful.  Not sure if Navicat 7 was wine based, but Navicat 8 is all but useless in a standard Compiz / Ubuntu scenario.

Keith

---

