---
title: "gretl on Ubuntu 11.04"
date: 2011-09-07
forum: Education &amp; Science
---

### Post by evenrelation on 2011-09-07
This is a complete numpty question for Ubuntu median user.

Gretl for Natty is broken, so I navigated to [packages.debian.org]("http://packages.debian.org/gretl") to get version 1.9.5.

The instructions for the package [[gretl_1.9.5.orig.tar.bz2]]("http://ftp.de.debian.org/debian/pool/main/g/gretl/gretl_1.9.5.orig.tar.bz2") say 

> Gretl uses GNU autoconf.  Here's the quick way to get going:

  ./configure
  make
  make check
  make install

* You may want to do "./configure --help" first to see what options are
  available.  

* By default the installation goes under /usr/local.  To install
  elsewhere use "./configure --prefix=/your/prefix". 

* On systems where GNU make is not the default you may need to use the
  "--with-gmake" option to ./configure.
  
See the Gretl User's Guide, Appendix C ("Building gretl") for further 
details [ [http://gretl.sourceforge.net/#man](http://gretl.sourceforge.net/#man) ] and when I follow them I get
```
username@username-laptop:~/Downloads/gretl-1.9.5$ ./configure
...
Long list of executions
...
Please install libxml2 and then reconfigure gretl.
libxml2 is available from http://xmlsoft.org/

username@username-laptop:~/Downloads/gretl-1.9.5$ make
make -C lib
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/lib'
../libtool --mode=compile gcc  -c -msse2 -g -O2 -I.. -I.. -I../lib/src     -I/usr/share/R/include   -DHAVE_CONFIG_H -DLIBDIR=\"/usr/local/lib\"    -o csvdata.lo ../lib/src/csvdata.c
libtool: compile:  gcc -c -msse2 -g -O2 -I.. -I.. -I../lib/src -I/usr/share/R/include -DHAVE_CONFIG_H -DLIBDIR=\"/usr/local/lib\" ../lib/src/csvdata.c  -fPIC -DPIC -o .libs/csvdata.o
../lib/src/csvdata.c:27:18: fatal error: glib.h: No such file or directory
compilation terminated.
make[1]: *** [csvdata.lo] Error 1
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/lib'
make: *** [lib] Error 2

```The package libxml2 is already installed, and I have no idea what to do with my other option, [[gretl_1.9.5-2.debian.tar.gz]]("http://ftp.de.debian.org/debian/pool/main/g/gretl/gretl_1.9.5-2.debian.tar.gz"), if that is what I should be using.

What's the obvious issue that I'm missing? How can I make gretl work on Natty?

---

### Post by evenrelation on 2011-09-09
I followed the instructions here: [http://lists.wfu.edu/pipermail/gretl-users/2011-February/005883.html](http://lists.wfu.edu/pipermail/gretl-users/2011-February/005883.html)

but got the following when I executed sudo make install:

```
username@username-laptop:~/Downloads/gretl-1.9.5$ sudo make install
make -C lib
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/lib'
make[1]: `libgretl-1.0.la' is up to date.
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/lib'
make -C cli
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/cli'
make[1]: `gretlcli' is up to date.
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/cli'
./builddate
build.h is current
make -C gui2
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/gui2'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/gui2'
make -C plugin
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/plugin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/plugin'
make -C po
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/po'
make -C share
make[1]: Entering directory `/home/username/Downloads/gretl-1.9.5/share'
make -C ../doc/commands help-all
make: Entering an unknown directory
make: *** ../doc/commands: No such file or directory. Stop.
make: Leaving an unknown directory
make[1]: *** [help] Error 2
make[1]: Leaving directory `/home/username/Downloads/gretl-1.9.5/share'
make: *** [share] Error 2

```

My only option is option 2 described here: [http://lists.wfu.edu/pipermail/gretl-users/2011-April/006175.html](http://lists.wfu.edu/pipermail/gretl-users/2011-April/006175.html) 

but I don't know how to add debian sid to my repo.

---

### Post by SeijiSensei on 2011-09-09
I'm on Kubuntu 10.10.

I just tried compiling 1.9.5 using both the source from Debian that you linked to and the source on the gretl site.  No matter what I tried, I couldn't get configure to find the lapack linear algebra libraries.  Ubuntu claims they are installed, but configure says they are not.

Did you try installing the Maverick packages for 1.9.0?  You need these:

gretl gretl-common gretl-data gretl-doc libgretl1 unixodbc

If you start at the [Maverick gretl page]("http://packages.ubuntu.com/maverick/gretl"), you'll see links to these other related packages in the lower left corner of the page.

1.9.0 works fine on my 10.10 system.

---

### Post by mdshaver on 2011-09-11
I would recommend simply installing gretl from Debian testing. You will need to install all dependencies individually. This may be annoying but it has worked successfully for me.

---

### Post by cpbl on 2011-09-12
Sadly, if you're running 11.04, the fastest way to just have a look to see whether you like gretl may be to download the Windows installer. You can launch/install gretl by launching that installer with wine (ie, from a shell prompt: wine gretl-xx.exe )

---

### Post by dougao06 on 2011-09-16
> **mdshaver said:**
> I would recommend simply installing gretl from Debian testing. You will need to install all dependencies individually. This may be annoying but it has worked successfully for me.

I quote that. I also had same problem as evenrelation, but I solved simply by changing source.list adding debian testing APTs and running sudo apt-get install -t debian.testing gretl.

Now I have gretl 1.9.5 and to the best of my knowledge it works fine.

ps: you might have to run apt-get build-dep gretl first.

---

### Post by jfca283 on 2012-01-16
When gretl will be fixed for ubuntu 11.04? i don't like running it from wine.

---

