---
title: "How do I update armagetron?"
date: 2006-09-26
forum: Gaming &amp; Leisure
---

### Post by Rafinator on 2006-09-26
I installed through add/remove but now can't figure out how to update.  If ound the newer packages on their website, but I don't know how to install with what they offer, I thought I needed a .deb file.

---

### Post by Perfect Storm on 2006-09-26
If there's .deb file and you are using dapper just double click it.

---

### Post by Rafinator on 2006-09-26
There isn't a deb file, that's what i'm saying, and the one in add/remove isn't the newest version.

---

### Post by Perfect Storm on 2006-09-26
Well, then you have to compile it if you want the latest version.
You have to download the source  for that. unpack it, read the Readme file (if it have one, good idea to see what the dudes says).

Install build-essential, run ./configure 
./configure --help would also be a good idea to run first to see what you can add and disable, alter how it shall compile it.
When you ran ./configure and downloaded the extra libs (-dev packages for the most), you run make afterwards.
Then you could make a fake .deb by running sudo checkinstall (requires checkinstall installed) or if it won't work just run sudo make install

Make sure to uninstall the previous version of armagetron first.

---

### Post by Rafinator on 2006-09-26
Alright, will try this later, there is an rpm, is there an easy way to install with this?  I know ubuntu normally doens't install with rpm's but I think i've heard of some tutorials in "tricking" ubuntu into installing with it.

---

### Post by Perfect Storm on 2006-09-26
You could try see if a converted .rpm package works (it might or it might not).
Uninstall previous armagetron package.
```
sudo aptitude install alien
cd /where/you/downloaded/the/package
sudo alien -i XXXXXXXXXXX.rpm
```

---

### Post by Rafinator on 2006-09-26
that's what I get.
```
rafinator@ubuntu:~$ sudo aptitude install alien
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.0 debconf-utils debhelper dpkg-dev gcc gcc-4.0
  html2text libbeecrypt6 libc6-dev librpm4 linux-kernel-headers make rpm
The following NEW packages will be installed:
  alien binutils cpp cpp-4.0 debconf-utils debhelper dpkg-dev gcc gcc-4.0
  html2text libbeecrypt6 libc6-dev librpm4 linux-kernel-headers make rpm
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6MB of archives. After unpacking 40.8MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper/main make 3.80+3.81.b4-1 [286kB]
Get:2 http://archive.ubuntu.com dapper/main binutils 2.16.1cvs20060117-1ubuntu2 [1406kB]
Get:3 http://archive.ubuntu.com dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get:4 http://archive.ubuntu.com dapper/main html2text 1.3.2a-3 [95.5kB]
Get:5 http://archive.ubuntu.com dapper/main debconf-utils 1.4.72ubuntu9 [30.9kB]Get:6 http://archive.ubuntu.com dapper/main debhelper 5.0.7ubuntu13 [506kB]
Get:7 http://archive.ubuntu.com dapper/main libbeecrypt6 4.1.2-4 [121kB]
Get:8 http://archive.ubuntu.com dapper/main librpm4 4.4.1-5ubuntu2 [933kB]
Get:9 http://archive.ubuntu.com dapper/main rpm 4.4.1-5ubuntu2 [597kB]
Get:10 http://archive.ubuntu.com dapper/main alien 8.64 [104kB]
Get:11 http://archive.ubuntu.com dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get:12 http://archive.ubuntu.com dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:13 http://archive.ubuntu.com dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get:14 http://archive.ubuntu.com dapper/main gcc 4:4.0.3-1 [5048B]
Get:15 http://archive.ubuntu.com dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18 [1039kB]
Get:16 http://archive.ubuntu.com dapper/main libc6-dev 2.3.6-0ubuntu20 [2822kB]
Fetched 10.6MB in 26s (401kB/s)
Selecting previously deselected package make.
(Reading database ... 72979 files and directories currently installed.)
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package binutils.
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.72ubuntu9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.7ubuntu13_all.deb) ...
Selecting previously deselected package libbeecrypt6.
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-4_i386.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.4.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.64_all.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Setting up make (3.80+3.81.b4-1) ...

Setting up binutils (2.16.1cvs20060117-1ubuntu2) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up html2text (1.3.2a-3) ...

Setting up debconf-utils (1.4.72ubuntu9) ...

Setting up debhelper (5.0.7ubuntu13) ...
Setting up libbeecrypt6 (4.1.2-4) ...

Setting up librpm4 (4.4.1-5ubuntu2) ...

Setting up rpm (4.4.1-5ubuntu2) ...

Setting up alien (8.64) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
rafinator@ubuntu:~$ cd /home/rafinator/
rafinator@ubuntu:~$ sudo alien -i armagetronad-0.2.8.2.1-1.i686-generic-linux-gnu.rpm
Warning: Skipping conversion of scripts in package armagetronad: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
rafinator@ubuntu:~$

```

---

### Post by Perfect Storm on 2006-09-27
Try:
```
sudo alien --scripts armagetronad-0.2.8.2.1-1.i686-generic-linux-gnu.rpm
sudo dpkg -i XXXXXXXXXXXXXXX.deb
```


If it doesn't work, you have to compile it.

---

### Post by Perfect Storm on 2006-09-27
Here: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=138&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=138&Itemid=63)

I wrote a howto compile, install and play the latest version of Armagetron Advanced.

---

### Post by bbrg548 on 2007-01-09
> **Artificial Intelligence said:**
> Here: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=138&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=138&Itemid=63)

I wrote a howto compile, install and play the latest version of Armagetron Advanced.

Everything works until I get to checkinstall, then I get this output:

This package will be built according to these values:

0 -  Maintainer: [ root@Jhereg ]
1 -  Summary: [ Armagetron Advanced ]
2 -  Name:    [ armagetronad ]
3 -  Version: [ 0.2.8.2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ armagetronad-0.2.8.2.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src'
Making install in first
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/first'
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/first'
make -C ../../ install-first
make[4]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
test -x /usr/local/bin/armagetronad-uninstall && /usr/local/bin/armagetronad-uninstall || true
error: package armagetronad is not installed
make[4]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/first'make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/first'Making install in doc
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc'
Making install in net
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc/net'
make[4]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc/net'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/games/armagetronad/html/net" || mkdir -p -- "/usr/local/share/doc/games/armagetronad/html/net"
 /usr/bin/install -c -m 644 'index.html' '/usr/local/share/doc/games/armagetronad/html/net/index.html'
 /usr/bin/install -c -m 644 'lower.html' '/usr/local/share/doc/games/armagetronad/html/net/lower.html'
 /usr/bin/install -c -m 644 'middle.html' '/usr/local/share/doc/games/armagetronad/html/net/middle.html'
 /usr/bin/install -c -m 644 'upper.html' '/usr/local/share/doc/games/armagetronad/html/net/upper.html'
make[4]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc/net'
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc/net'
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc'
make[4]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/games/armagetronad/html" || mkdir -p -- "/usr/local/share/doc/games/armagetronad/html"
 /usr/bin/install -c -m 644 'bugs.html' '/usr/local/share/doc/games/armagetronad/html/bugs.html'
 /usr/bin/install -c -m 644 'changelog.html' '/usr/local/share/doc/games/armagetronad/html/changelog.html'
 /usr/bin/install -c -m 644 'commands.html' '/usr/local/share/doc/games/armagetronad/html/commands.html'
 /usr/bin/install -c -m 644 'compile.html' '/usr/local/share/doc/games/armagetronad/html/compile.html'
 /usr/bin/install -c -m 644 'config.html' '/usr/local/share/doc/games/armagetronad/html/config.html'
 /usr/bin/install -c -m 644 'faq.html' '/usr/local/share/doc/games/armagetronad/html/faq.html'
 /usr/bin/install -c -m 644 'index.html' '/usr/local/share/doc/games/armagetronad/html/index.html'
 /usr/bin/install -c -m 644 'install_linux.html' '/usr/local/share/doc/games/armagetronad/html/install_linux.html'
 /usr/bin/install -c -m 644 'install_macosx.html' '/usr/local/share/doc/games/armagetronad/html/install_macosx.html'
 /usr/bin/install -c -m 644 'install_result.html' '/usr/local/share/doc/games/armagetronad/html/install_result.html'
 /usr/bin/install -c -m 644 'install_windows.html' '/usr/local/share/doc/games/armagetronad/html/install_windows.html'
 /usr/bin/install -c -m 644 'network.html' '/usr/local/share/doc/games/armagetronad/html/network.html'
 /usr/bin/install -c -m 644 'readme_macosx.html' '/usr/local/share/doc/games/armagetronad/html/readme_macosx.html'
 /usr/bin/install -c -m 644 'todo.html' '/usr/local/share/doc/games/armagetronad/html/todo.html'
 /usr/bin/install -c -m 644 'versions.html' '/usr/local/share/doc/games/armagetronad/html/versions.html'
make[4]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc'
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc'
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/doc'
Making install in thirdparty
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty'
Making install in particles
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[4]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty/particles'
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty'
make[4]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty'
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty'
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src/thirdparty'
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src'
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'armagetronad_main' '/usr/local/bin/armagetronad_main'
/usr/bin/install: setting permissions for `/usr/local/bin/armagetronad_main': No such file or directory
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src'
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src'
make[1]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/src'
Making install in resource
make[1]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/resource'make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/resource'make[2]: Nothing to be done for `install-exec-am'.
if test -d included; then\
                ln -sf included linked_included.install;\
        else\
                ln -sf ./included linked_included.install;\
        fi
mkdir -p /usr/local/share/games/armagetronad/resource/included
cp -LR linked_included.install/* /usr/local/share/games/armagetronad/resource/included
find /usr/local/share/games/armagetronad/resource -type d -exec chmod 755 \{\} \;
find /usr/local/share/games/armagetronad/resource -type f -exec chmod 644 \{\} \;
rm -f linked_included.install
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/resource'
make[1]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/resource'
Making install in batch
make[1]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/batch'
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/batch'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/games/armagetronad/scripts" || mkdir -p -- "/usr/local/share/games/armagetronad/scripts"
 /usr/bin/install -c 'sysinstall' '/usr/local/share/games/armagetronad/scripts/sysinstall'
 /usr/bin/install -c 'relocate' '/usr/local/share/games/armagetronad/scripts/relocate'
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/batch'
make[1]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/batch'
Making install in config
make[1]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/config'
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/config'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/etc/games/armagetronad" || mkdir -p -- "/usr/local/etc/games/armagetronad"
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'default.cfg' '/usr/local/etc/games/armagetronad/default.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'master.srv' '/usr/local/etc/games/armagetronad/master.srv'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'settings.cfg' '/usr/local/etc/games/armagetronad/settings.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'settings_visual.cfg' '/usr/local/etc/games/armagetronad/settings_visual.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'settings_dedicated.cfg' '/usr/local/etc/games/armagetronad/settings_dedicated.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'aiplayers.cfg' '/usr/local/etc/games/armagetronad/aiplayers.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'rc.config' '/usr/local/etc/games/armagetronad/rc.config'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/breakfast_in_hell.cfg' '/usr/local/etc/games/armagetronad/examples/breakfast_in_hell.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/single_use_turbo.cfg' '/usr/local/etc/games/armagetronad/examples/single_use_turbo.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/fortress_soccer.cfg' '/usr/local/etc/games/armagetronad/examples/fortress_soccer.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/death_zone.cfg' '/usr/local/etc/games/armagetronad/examples/death_zone.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/cvs_test/fortress_physics.cfg' '/usr/local/etc/games/armagetronad/examples/cvs_test/fortress_physics.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/cvs_test/fortress_scoring.cfg' '/usr/local/etc/games/armagetronad/examples/cvs_test/fortress_scoring.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/cvs_test/fortress_politics.cfg' '/usr/local/etc/games/armagetronad/examples/cvs_test/fortress_politics.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/cvs_test/fortress_complete.cfg' '/usr/local/etc/games/armagetronad/examples/cvs_test/fortress_complete.cfg'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'examples/cvs_test/sumo_complete.cfg' '/usr/local/etc/games/armagetronad/examples/cvs_test/sumo_complete.cfg'
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/config'
make[1]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/config'
Making install in desktop
make[1]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/desktop'
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/desktop'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/games/armagetronad/desktop" || mkdir -p -- "/usr/local/share/games/armagetronad/desktop"
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'armagetronad.desktop' '/usr/local/share/games/armagetronad/desktop/armagetronad.desktop'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'icons/small/armagetronad.png' '/usr/local/share/games/armagetronad/desktop/icons/small/armagetronad.png'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'icons/medium/armagetronad.png' '/usr/local/share/games/armagetronad/desktop/icons/medium/armagetronad.png'
 /home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c -m 644 'icons/large/armagetronad.png' '/usr/local/share/games/armagetronad/desktop/icons/large/armagetronad.png'
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/desktop'
make[1]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1/desktop'
make[1]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
make[2]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
make  install-exec-hook
make[3]: Entering directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
/home/jake/Desktop/armagetronad-0.2.8.2.1/install-sh -c batch/make/uninstall /usr/local/bin/armagetronad-uninstall
rm /usr/local/bin/armagetronad-uninstall
MAKE="make" PREFIX="/usr/local" PROGTITLE="Armagetron Advanced" SCRIPTDIR="/usr/local/share/games/armagetronad/scripts" sh batch/make/uninstall /usr/local/bin/armagetronad-uninstall ""
Generating uninstallation script /usr/local/bin/armagetronad-uninstall.../bin/sh: /usr/local/armatempbin/rm: /bin/sh: bad interpreter: No such file or directory/bin/sh: /usr/local/armatempbin/rm: /bin/sh: bad interpreter: No such file or directory
/bin/sh: /usr/local/armatempbin/rm: /bin/sh: bad interpreter: No such file or directory
/bin/sh: /usr/local/armatempbin/rm: /bin/sh: bad interpreter: No such file or directory
make[7]: *** [uninstall-htmlDATA] Error 126
make[6]: *** [uninstall-recursive] Error 1
make[5]: *** [uninstall-recursive] Error 1
make[4]: *** [uninstall-recursive] Error 1
make[3]: *** [install-uninstall] Error 1
make[3]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
make[2]: *** [install-exec-am] Error 2
make[2]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jake/Desktop/armagetronad-0.2.8.2.1'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


-Jake

---

### Post by inthepit on 2007-01-09
this is what did it for me:

download the bin file on the [armagetronad site](http://www.armagetronad.net/downloads.php) and then:

```
sudo apt-get update
sudo apt-get install libstdc++5 libsdl-image1.2
cd Desktop
chmod 755 armagetronad-0.2.8.2.1.i686-generic-linux-gnu.package
bash ./armagetronad-0.2.8.2.1.i686-generic-linux-gnu.package -t
```

i can't take the credit.  i found it here: [http://forums.armagetronad.net/viewtopic.php?p=107941#107941](http://forums.armagetronad.net/viewtopic.php?p=107941#107941)

---

### Post by Perfect Storm on 2007-01-09
If checkinstall fail use sudo make install instead.

---

