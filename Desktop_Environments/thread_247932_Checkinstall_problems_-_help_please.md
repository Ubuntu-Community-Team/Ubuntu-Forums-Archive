---
title: "Checkinstall problems - help please"
date: 2006-08-31
forum: Desktop Environments
---

### Post by shaggly on 2006-08-31
Hi guys,

I've been experimenting with a few distros, and I'm quite settled with Kubuntu. It's nice to be here :D 

I've searched around to try and find a solution to this problem I keep having, but I can't find anything. Not only that but a Google search on some of the key error wordings only yield a couple of results with no definitive solution or explanation.

Running Dapper 6.06, with "build essential", "fakeroot", and the necessary headers. I can compile from source and install that way (verified), but checkinstall keeps on confounding me. I've tried two packages that I have the binaries for, and that I have proven out to work on previous installs. They are for my modem, and are ungrab-winmodem and the driver.

I untar the files. Then I do a make (as user), and then upon checkinstall (sudo) I get errors. I've tried all different combinations of this. I've tried compiling as root, sudoing the make in a home folder, and then sudoing the checkinstall, etc etc.

Here's a transcript; hopefully one of you kind sirs will be nice enough to help me out with some hints... I know it must be something simple, but it's driving me round the bend.


> 
martin@martin-kubuntu:~/Stuff/temporary/Installers/modems/ungrab-winmodem$ ls
doc-pak  Makefile  Readme.txt  ungrab-winmodem.c
martin@martin-kubuntu:~/Stuff/temporary/Installers/modems/ungrab-winmodem$ sudo make
make modules -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/martin/Stuff/temporary/Installers/modems/ungrab-winmodem
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/martin/Stuff/temporary/Installers/modems/ungrab-winmodem/ungrab-winmodem.o
  Building modules, stage 2.
  MODPOST
  CC      /home/martin/Stuff/temporary/Installers/modems/ungrab-winmodem/ungrab-winmodem.mod.o
  LD [M]  /home/martin/Stuff/temporary/Installers/modems/ungrab-winmodem/ungrab-winmodem.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
martin@martin-kubuntu:~/Stuff/temporary/Installers/modems/ungrab-winmodem$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

The checkinstallrc file was not found at:
/usr/local/lib/checkinstall/checkinstallrc

Assuming default values.


Please choose the packaging method you want to use.
Slackware [S], RPM [R] or Debian [D]? d


Please write a description for the package.
End your description with an empty line or EOF.
>> A module utility for releasing serial modem ports
>>

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "winmodem" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values:

0 -  Maintainer: [ root@martin-kubuntu ]
1 -  Summary: [ A module utility for releasing serial modem ports ]
2 -  Name:    [ ungrab ]
3 -  Version: [ winmodem ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ungrab-winmodem ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 3
Enter new version:
>> 1

This package will be built according to these values:

0 -  Maintainer: [ root@martin-kubuntu ]
1 -  Summary: [ A module utility for releasing serial modem ports ]
2 -  Name:    [ ungrab ]
3 -  Version: [ 1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ungrab-winmodem ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
pwd: couldn't find directory entry in `../../../../../../../..' with matching i-node
make modules -C /lib/modules/2.6.15-23-386/build SUBDIRS=
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
  CHK     include/linux/version.h
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
shell-init: error retrieving current directory: getcwd: cannot access parent directories: Invalid argument
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make: *** [all] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

 

For some reason, it cannot use pwd to find the directory to insert into SUBDIRS.

Any clues please?

---

### Post by shaggly on 2006-09-04
I don't suppose anyone out there couuld take a couple of minutes to read thorugh this, and suggest why I am having these PWD problems when trying to checkinstall **PLEASE**???

---

