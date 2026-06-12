---
title: "How to install vlc-1.1.11.tar.bz2 in ubuntu 11.04?"
date: 2011-09-15
forum: Desktop Environments
---

### Post by Fahim.pk on 2011-09-15
Hi, i have recently installed ubuntu natty. I do not have an internet connection for that computer, therefore i cant download softs directly through software center. I downloaded vlc player from softopedia.. Which is in tar.bz2 format, but i cant install it. Please post step by step installation procedure for vlc 1.11.1. Please please

---

### Post by raja.genupula on 2011-09-15
i think you are going to need build essential tools for that , have you installed them on the computer ? 

actually the process can be as this 
```
./configure
```
```
make 
```
```
sudo make install 
```
this is the way of installation from source

actually every source going to have a readme text file , in that they gonna explain how to install form source . look at that for more details ,.

---

### Post by fdrake on 2011-09-15
hello raja.genupula! :D
@OP
follow raja.genupula's commands if you encounter some error msgs run this command first and then try again to compile from source
```

sudo aptitude install gcc make build-essential dpkg-dev patch dmks

```

---

### Post by Fahim.pk on 2011-09-15
i am very new to Linux and do not know how to apply these codes. previously i used Windows, in which i just used to click on Next, Next, Next and finish. please post in details. I can not understand "Install" file in the package . the file reads.

'INSTALL file for the VLC media player

More extensive information for *nix, Windows, Mac OS X and BeOS users can be
found here: [http://developers.videolan.org/vlc/](http://developers.videolan.org/vlc/)

Bootstrapping VLC
=================

If you retrieved VLC from the git server and do not have a "configure"
script, please refer to the HACKING file.

Configuring VLC
===============

A typical way to configure VLC is:

   ./configure --prefix=/usr

See `./configure --help' for more information.

If you intend to debug stuff, you may want to compile with debugging
symbols:

   make distclean ; ./configure --prefix=/usr --enable-debug

We recommend using GCC to build VLC, though some people reported success
with the Intel C compiler (version 8) as well. GCC version 3.3 or higher is
required. On older systems (e.g. FreeBSD 4.x, BeOS), please select a more
recent version manually by setting the CC and CXX environment variables
appropriately while running the ./configure shell script.


Building VLC
============

Once configured, run `make' to build VLC.


Installing and running VLC
==========================

You can install the VLC and its plugins by typing:

   make install

But you don't need to install it if you don't want to; VLC can be launched
from the current directory as well:

   ./vlc


Building packages
=================

To build a Debian package, you need to get the packaging info
   git clone git://git.debian.org/pkg-multimedia/vlc.git debian
and then
   git-buildpackage


To build RPM packages, copy a spec file from extra/package/rpm and:

   rpm -ba vlc.spec

To build an ipkg package (iPAQ familiar Linux), use:

   ipkg-buildpackage" ????????????????????????

---

### Post by fdrake on 2011-09-15
right click the archive extract. open the folder > right click inside the folder > open terminal > run the commands posted in the previous posts.
if you have problem post here. you can also install vlc from your repositories with
```

sudo apt-get install vlc

```

---

### Post by raja.genupula on 2011-09-15
hey man , go with this 
copy that tar to home folder
open your terminal

```
tar xvf your_filename
```

2. cd to extracted folder
3.run all this one by one 

./configure
make 
sudo make install

all three separate commands run one by one 
post here the errors if you got any 

all the best , i hope you will get it .

---

### Post by Fahim.pk on 2011-09-15
After I applied ./configure===========>

{{{{{{{{{.....................checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?
fahim@ubuntu:~/vlc-1.1.11$ make
make: *** No targets specified and no makefile found.  Stop.
fahim@ubuntu:~/vlc-1.1.11$ sudo make install
[sudo] password for fahim: 
make: *** No rule to make target `install'.  Stop.
fahim@ubuntu:~/vlc-1.1.11$ }}}}}}}




         Now what should I do?

---

### Post by fdrake on 2011-09-15
> **Fahim.pk said:**
> After I applied ./configure===========>

{{{{{{{{{.....................checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?
fahim@ubuntu:~/vlc-1.1.11$ make
make: *** No targets specified and no makefile found.  Stop.
fahim@ubuntu:~/vlc-1.1.11$ sudo make install
[sudo] password for fahim: 
make: *** No rule to make target `install'.  Stop.
fahim@ubuntu:~/vlc-1.1.11$ }}}}}}}
         Now what should I do?

you have some dependecies problem. run this command:
```

sudo aptitude install libdbus-1-3 libdbus-1-dev

```

if you still encounter msg like this one just install the program from the repo, it will automatically install the dependencies neede for you. check my previous post.

---

### Post by raja.genupula on 2011-09-16
[http://www.ubuntugeek.com/vlc-1-1-7-released-and-ubuntu-ppa-installation-instructions-included.html](http://www.ubuntugeek.com/vlc-1-1-7-released-and-ubuntu-ppa-installation-instructions-included.html)

---

### Post by ottosykora on 2011-09-16
@fdrake

have you seen that the OP has no internet connection on his computer?

In that case all aptitude cammands are of little use for him...

---

### Post by raja.genupula on 2011-09-16
hey man download this files from  another system which have internet and install them in your system 
[http://packages.ubuntu.com/natty/libdbus-1-dev](http://packages.ubuntu.com/natty/libdbus-1-dev)

download all those things and install in your system 
and then try again what i suggest you .

---

### Post by Fahim.pk on 2011-09-16
I have not any internet conection in my pc & i want to install from source file.(vlc.tar.bz2). I downloaded vlc player from softopedia.com. I am using ubuntu 11.04 natty.

---

### Post by raja.genupula on 2011-09-16
hey man 
thats why i have given these things to you .
go to internet center and get them download and bring back to your pc by using a pen drive and then install . to do all these things you dont need any internet connection to your pc . 

all the best man

---

### Post by haqking on 2011-09-16
As long as you have the correct dependancies then follow this:

[http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux](http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux)

if you are required dependancies then you will need to somehow get them to your machine as you have no method of doing a apt-get

---

### Post by raja.genupula on 2011-09-16
> **haqking said:**
> As long as you have the correct dependancies then follow this:

[http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux](http://linuxers.org/howto/how-install-vlc-11-compiling-git-ubuntu-linux)

if you are required dependancies then you will need to somehow get them to your machine as you have no method of doing a apt-get

+1 
its have everything you need

---

### Post by oldos2er on 2011-09-16
Rather than installing from source, use Keryx if you have access to another computer with internet. [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by raja.genupula on 2011-09-16
after seeing a issue like this i got an idea. 
i think its not possible, but where i can share and clarify , only here .

what if we have something like this ? 
taking the dump of the software which is installed in another system and make it work in our system. 

i know we have to take out from each every folder of filesystem 
and its a impossible thing .
just its an idea .

---

### Post by ottosykora on 2011-09-17
here we can see one of the big problems of linux.

The software for windows, one file, works simply out of the box, on all current windows versions without any extras.

For linux, the vlc has to provide number of versions for each distro separate and it still does not work as we can see without lot of work, and internet connection.

This is not the fault of the present day devs, but in the past days all those devs forget simply to take care of one common structure and basic 'must have' content of any distro.
This ended in such chaos as we have today.

---

### Post by raja.genupula on 2011-09-17
what if we have a .deb for vlc in ubuntu which have all required dependencies . if we make this , then user no need to download from the internet and everything can be done with that file it self .

---

### Post by haqking on 2011-09-17
> **ottosykora said:**
> here we can see one of the big problems of linux.

The software for windows, one file, works simply out of the box, on all current windows versions without any extras.

For linux, the vlc has to provide number of versions for each distro separate and it still does not work as we can see without lot of work, and internet connection.

This is not the fault of the present day devs, but in the past days all those devs forget simply to take care of one common structure and basic 'must have' content of any distro.
This ended in such chaos as we have today.


That is down to the VLC developers not Windows or Linux.

Also there are lots of things you install in Windows that rely on say the .net framework or a certain service pack.

So the dependency issue is not Linux centric by any means.

---

### Post by ottosykora on 2011-09-17
>what if we have a .deb for vlc in ubuntu which have all required dependencies . <

well yes , thsi would solve it, but I know that there were times when some people tried to do this by providing portable apps for linux. They tried to simply include all needed parts, ending up with very big volume of something.

But it could be done sure, for just some deb derivates or so probably.

---

### Post by ottosykora on 2011-09-17
>That is down to the VLC developers not Windows or Linux.

Also there are lots of things you install in Windows that rely on say the .net framework or a certain service pack.<

yes those .net unfinished software does come up now with this .net feature. If someone has to make something just for one version of .net , then well he does not need to be considered as delivering something useful.

What I mean, is that for windows, normal, commercial or otherwise reasonably compiled software will work on any current version of windows.
One can just download it , run the installer or what ever and it is here.

As this can not be done under linux, is just the matter of extreme chaos, apparently no rules what should a distro contain in minimum etc. This ends up in the fact, that installation of average program is possible only with solid internet connection and this is what I call wrong.

Some time ago, it was easy possible to install even ubuntu from the CD and without any internet connection. Now even this is not possible to be done properly.

---

### Post by raja.genupula on 2011-09-17
Oh this is going to some where else . Hey fahim, have you installed vlc in your system ?

---

