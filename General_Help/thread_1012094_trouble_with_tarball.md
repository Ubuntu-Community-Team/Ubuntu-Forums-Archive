---
title: "trouble with tarball"
date: 2008-12-15
forum: General Help
---

### Post by rusty_jones on 2008-12-15
```
rusty@rusty-green:~$ sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rusty@rusty-green:~$ cd ktorrent-3.1.5
rusty@rusty-green:~/ktorrent-3.1.5$ ./configure
bash: ./configure: No such file or directory
rusty@rusty-green:~/ktorrent-3.1.5$ make
make: *** No targets specified and no makefile found.  Stop.
rusty@rusty-green:~/ktorrent-3.1.5$ 


```

I'm trying to upgrade ktorrent to the newest release. I currently have 3.1.2    i uncompressed the tarball and got a dir. ktorrent-3.1.5. I tried ./configure with no luck. Can anyone tell me whats going on?

Rusty

---

### Post by taurus on 2008-12-15
What's the output of this command from a terminal?

```
ls -la ~/ktorrent-3.1.5
```

By the way, don't have to install make by itself.  Just install the build-essential package if you plan to build something from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by logos34 on 2008-12-15
look inside the folder for instructions -- README.txt or INSTALL.txt.  You may be able to just save it your home dir and run it with ./

edit: just checked it myself--neither is there.  Maybe build-essential is the problem, but then there's no make file in the archive (?)

---

### Post by rusty_jones on 2008-12-15
```
rusty@rusty-green:~$ ls -la ~/ktorrent-3.1.5
total 92
drwxr-xr-x 12 rusty rusty  4096 2008-11-15 06:11 .
drwxr-xr-x 56 rusty rusty  4096 2008-12-15 13:28 ..
-rw-r--r--  1 rusty rusty 16728 2008-11-15 06:08 ChangeLog
drwxr-xr-x  3 rusty rusty  4096 2008-11-15 06:08 cmake
-rw-r--r--  1 rusty rusty  1507 2008-11-15 06:11 CMakeLists.txt
-rw-r--r--  1 rusty rusty 18273 2008-11-15 06:08 COPYING
drwxr-xr-x  2 rusty rusty  4096 2008-11-15 06:08 ideal
drwxr-xr-x  3 rusty rusty  4096 2008-11-15 06:08 ktorrent
drwxr-xr-x  2 rusty rusty  4096 2008-11-15 06:08 ktupnptest
drwxr-xr-x 15 rusty rusty  4096 2008-11-15 06:08 libbtcore
drwxr-xr-x  6 rusty rusty  4096 2008-11-15 06:08 libktcore
drwxr-xr-x  2 rusty rusty  4096 2008-11-15 06:08 libktupnp
drwxr-xr-x 14 rusty rusty  4096 2008-11-15 06:08 plugins
drwxr-xr-x 26 rusty rusty  4096 2008-11-15 06:11 po
drwxr-xr-x  2 rusty rusty  4096 2008-11-15 06:08 templates

```

build-essentials is the newest version.

Rusty

---

### Post by logos34 on 2008-12-15
ah, here we go:
> 
[http://ktorrent.org/?q=downloads](http://ktorrent.org/?q=downloads)

Compiling and installing KTorrent version 3.0.0 or later :

tar -xvjf ktorrent-3.X.Y.tar.bz2
cd ktorrent-3.X.Y
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
sudo make install

You will need to install **cmake** and all the necessary development packages (Qt,KDE,libgmp,QCA2), to get it compiled properly.

---

### Post by rusty_jones on 2008-12-15
```
W: Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/intrepid-security/Release  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

```
 
I did get this error at the end of update.

Rusty

---

### Post by taurus on 2008-12-15
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by rusty_jones on 2008-12-15
```
rusty@rusty-green:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiversedeb http://ppa.launchpad.net/tualatrix/ubuntu intrepid
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

```

Rusty

---

### Post by taurus on 2008-12-15
> **rusty_jones said:**
> ```
rusty@rusty-green:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse**[COLOR="Blue"]deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid[/COLOR]**
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

```

Rusty

That one in blue should be on a separate line.

```
gksudo gedit /etc/apt/sources.list
```
Save the change and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rusty_jones on 2008-12-15
```
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
```

```
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
```

I changed the line above and i'm getting another error.

---

### Post by taurus on 2008-12-15
Post your new /etc/apt/sources.list again.

---

### Post by rusty_jones on 2008-12-15
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

```

---

### Post by rusty_jones on 2008-12-15
found the problem with the error. line 54 was missing main at the end.

---

### Post by rusty_jones on 2008-12-15
```
tar -xvjf ktorrent-3.X.Y.tar.bz2
cd ktorrent-3.X.Y
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
sudo make install
```

```
rusty@rusty-green:~/ktorrent-3.1.5/build$ make
make: *** No targets specified and no makefile found.  Stop.

```

I've gotten as far as make when i get this last error. I don't know where to go with this.

Rusty

---

### Post by mc4man on 2008-12-15
You need to have a kde4.x environment. The line your using should reflect this...

cmake -DCMAKE_INSTALL_PREFIX=[COLOR="Red"]/path/to/prefix/of/kde4/installation ..
[/COLOR]
I don't have kde4.x nor kubuntu so can't help you further there, if you where building a 3.x version I'd image you could do so fairly easily on ubuntu/gnome

---

