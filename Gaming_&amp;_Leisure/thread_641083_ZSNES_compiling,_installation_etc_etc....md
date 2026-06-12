---
title: "ZSNES compiling, installation etc etc..."
date: 2007-12-15
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2007-12-15
Don't know if this is the right section but please help if anybody can. I'm trying to install Zsnes (SNES emulator) from a tar.bz2 archive. I open the archive and see the source folder (src) etc...I read the read me included with it but it's very poorly explained and it's confusing. Can anybody tell me how to compile, build etc. the emulator? by the way if this helps my Zsnes folder is on Desktop. /home/gedg/Desktop...thanks in advance...

---

### Post by po0f on 2007-12-15
Moonfrost,

(Run the commands below from a terminal.)

```
$ sudo apt-get build-dep zsnes
$ tar xjf /path/to/zsnes151src.tar.bz2
$ cd zsnes_1_51/src
$ ./configure
$ make
```

At this point, you can run zsnes from current directory with:

```
$ ./zsnes
```

To install normally:

```
$ sudo make install
```

To install as deb (recommended):

```
$ sudo apt-get install checkinstall
$ sudo checkinstall --pkgname zsnes --pkgversion 1.510
```

You do know zsnes is [in the repos](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zsnes&searchon=names&subword=1&version=all&release=all), right?  ;)

---

### Post by Moonfrost on 2007-12-15
> **po0f said:**
> Moonfrost,

(Run the commands below from a terminal.)

```
$ sudo apt-get build-dep zsnes
$ tar xjf /path/to/zsnes151src.tar.bz2
$ cd zsnes_1_51/src
$ ./configure
$ make
```

At this point, you can run zsnes from current directory with:

```
$ ./zsnes
```

To install normally:

```
$ sudo make install
```

To install as deb (recommended):

```
$ sudo apt-get install checkinstall
$ sudo checkinstall --pkgname zsnes --pkgversion 1.510
```

You do know zsnes is [in the repos](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zsnes&searchon=names&subword=1&version=all&release=all), right?  ;)

Yeah I know it's on the reps but I had an issue with certain software from reps (including Zsnes) which I downloaded separetely and they worked so I wanted to see if this way problem will go away, thanks for your help!

---

### Post by Saghaulor on 2008-01-02
I followed poof's instructions and received the following error.

stephen@ubuntu:~$ cd /home/stephen/Desktop/zsnes*
stephen@ubuntu:~/Desktop/zsnes_1_51$ dir
docs  src
stephen@ubuntu:~/Desktop/zsnes_1_51$ cd /home/stephen/Desktop/zsnes*/src
stephen@ubuntu:~/Desktop/zsnes_1_51/src$ sudo make install
make: *** No rule to make target `install'.  Stop.
stephen@ubuntu:~/Desktop/zsnes_1_51/src$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-elementtree liblzo1 libboost-date-time1.34.1 python-mutagen
  python-qt3 python-sip4 libboost-thread1.34.1 libxmp2 python-pyvorbis
  python-pysqlite2 python-pyogg
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 118kB of archives.
After unpacking 561kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe checkinstall 1.6.1-4ubuntu1 [118kB]
Fetched 118kB in 1s (96.6kB/s)      
Selecting previously deselected package checkinstall.
(Reading database ... 108030 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.1-4ubuntu1_amd64.deb) ...
Setting up checkinstall (1.6.1-4ubuntu1) ...
stephen@ubuntu:~/Desktop/zsnes_1_51/src$ sudo checkinstall --pkgname zsnes --pkgversion 1.510

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> zsnes
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ zsnes ]
2 -  Name:    [ zsnes ]
3 -  Version: [ 1.510 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ src ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

stephen@ubuntu:~/Desktop/zsnes_1_51/src$

---

### Post by FranMichaels on 2008-01-02
> **Saghaulor said:**
> I followed poof's instructions and received the following error.

Not exactly :(. You never did ./configure, although I'd advise ./autogen.sh

Also, you don't need to put the full directory with cd
for example
let's say I have a folder called zsnes, with a subdirectory src I can do
cd zsnes
cd src

You can use cd ..
to go up a dir

cd -
to go to previous directories

Just thought I'd mention that is it makes life easier (also pressing tab to complete the dirs and some commands for you too. Press tab twice to get a list if there are multiple options, i.e. you have a folder called doc and dow, and you just typed do)

With that said,

Look at Dfreer's [how-to]("http://ubuntuforums.org/showthread.php?t=588744"), it covers building both 32-bit and amd64 versions of zsnes 1.51 with libao and release enabled. It's the best way to go!

---

### Post by Saghaulor on 2008-01-04
I found this site and tried what it instructed, and bam, I got it working.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64)

---

### Post by Vamp898 on 2008-01-04
Why dont use APT???


apt-get install zsnes

and it works

---

