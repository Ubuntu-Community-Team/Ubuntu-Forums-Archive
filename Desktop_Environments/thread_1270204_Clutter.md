---
title: "Clutter"
date: 2009-09-19
forum: Desktop Environments
---

### Post by aikiwolfie on 2009-09-19
I was trying to install Clutter on virtual machine. But it just doesn't work. I think I'm missing quite a few thing I need before I can install straight from a cloned git repository.

The Moblin web site has a few instructions on how to get things working. But as I said above. It doesn't work on my VM.

I'm running Ubuntu i386 in a VirtualBox VM with guest additions installed. It's a completely fresh install. I did install build-essentials and some packages that had clutter in their names (I'm guessing and stabbing in the dark here). Can't remember all of their names though.

Here's the commands I'm using and the output they give me.

```

#	Install Dependencies
#
sudo apt-get -y install libclutter-0.8-0
sudo apt-get -y install git-core
#
#	Set Install Path.
#
sudo mkdir /opt/clutter
export PREFIX=/opt/clutter
#
#	Download Clutter Source
#
git clone git://git.clutter-project.org/clutter
git clone git://git.clutter-project.org/clutter-box2d
#
#	Build Clutter Projects
#
cd clutter
./autogen.sh --prefix=$PREFIX
make
sudo make install
cd ../clutter-box2d
./autogen.sh --prefix=$PREFIX
make
sudo make install
```
```
*** No gtk-doc support ***
Symlinking file mkinstalldirs
Symlinking file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 188.
Use of uninitialized value $libtoolize in pattern match (m//) at /usr/bin/autoreconf line 188.
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  -I build/autotools
configure.ac:776: warning: macro `AM_SILENT_RULES' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:83: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:84: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
./autogen.sh: 2: gtkdocize: not found
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Clutter Build Script has finished ...
lynchk@Ubuntu-32-VM-00:~$ sudo rm -fvr /opt/clutter
[sudo] password for lynchk: 
removed directory: `/opt/clutter'
lynchk@Ubuntu-32-VM-00:~$ sudo rm -fvr /cutter
lynchk@Ubuntu-32-VM-00:~$ sudo rm -fvr /cutter-box2d
lynchk@Ubuntu-32-VM-00:~$ ls
clutter  clutter-box2d  Desktop  Documents  examples.desktop  Music  Pictures  Public  Scripts  Templates  Videos
lynchk@Ubuntu-32-VM-00:~$ sudo rm -fvr /clutter-box2d
lynchk@Ubuntu-32-VM-00:~$ ls
clutter  clutter-box2d  Desktop  Documents  examples.desktop  Music  Pictures  Public  Scripts  Templates  Videos
lynchk@Ubuntu-32-VM-00:~$ sudo rm -fr clutter
lynchk@Ubuntu-32-VM-00:~$ ls
clutter-box2d  Desktop  Documents  examples.desktop  Music  Pictures  Public  Scripts  Templates  Videos
lynchk@Ubuntu-32-VM-00:~$ sudo rm -fr clutter-box2d
lynchk@Ubuntu-32-VM-00:~$ ls
Desktop  Documents  examples.desktop  Music  Pictures  Public  Scripts  Templates  Videos
lynchk@Ubuntu-32-VM-00:~$ sudo /home/lynchk/Scripts/Bash/build-clutter-amd64-ubuntu-9.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libclutter-0.8-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Initialized empty Git repository in /home/lynchk/clutter/.git/
remote: Counting objects: 26716, done.
remote: Compressing objects: 100% (11491/11491), done.
remote: Total 26716 (delta 21694), reused 18706 (delta 15201)
Receiving objects: 100% (26716/26716), 7.22 MiB | 99 KiB/s, done.
Resolving deltas: 100% (21694/21694), done.
Initialized empty Git repository in /home/lynchk/clutter-box2d/.git/
remote: Counting objects: 1112, done.
remote: Compressing objects: 100% (512/512), done.
remote: Total 1112 (delta 672), reused 982 (delta 583)
Receiving objects: 100% (1112/1112), 1.11 MiB | 68 KiB/s, done.
Resolving deltas: 100% (672/672), done.
*** No gtk-doc support ***
Symlinking file mkinstalldirs
Symlinking file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 188.
Use of uninitialized value $libtoolize in pattern match (m//) at /usr/bin/autoreconf line 188.
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  -I build/autotools
configure.ac:776: warning: macro `AM_SILENT_RULES' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:83: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:84: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
./autogen.sh: 2: gtkdocize: not found
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.

```

---

