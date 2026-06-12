---
title: "ktorrent upgrade"
date: 2008-12-16
forum: General Help
---

### Post by rusty_jones on 2008-12-16
Ubuntu ver.8.10
Ktorrent 3.1.2
KDE 4.1.3

I tried upgrading to version 3.1.5. I followed the instuctions from ktorrent web site and got as far as "make." Then I got this message.

```
rusty@rusty-green:~/ktorrent-3.1.5/build$ make
make: *** No targets specified and no makefile found.  Stop.
```

here are the instructions from ktorrent web site. I'm also new to linux so please explain.

Rusty

---

### Post by SuperSonic4 on 2008-12-16
```
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
sudo make install
```

^ from the KTorrent website (and have you tried looking into kubuntu if you want the KDE desktop?)
Most KDE4 apps use cmake to compile now ```
sudo apt-get install cmake
``` and in general you will want to ```

cd *extracted tarball*
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
sudo make install
``` although the install.txt or readme.txt should be used as first reference. Using the repos or a deb is even better

---

### Post by rusty_jones on 2008-12-16
```
tar -xvjf ktorrent-3.X.Y.tar.bz2
cd ktorrent-3.X.Y
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
sudo make install
```

This was the the info from ktorrent for version 3.1.5

---

### Post by rusty_jones on 2008-12-16
And when I get to make is where i get the error from above```
rusty@rusty-green:~/ktorrent-3.1.5/build$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by utkjamie on 2009-01-19
If you haven't had any luck upgrading to 3.1.5, you might want to take an extreme route and try using the Debian Sid repository ([http://packages.debian.org/sid/i386/ktorrent/download](http://packages.debian.org/sid/i386/ktorrent/download)). I wouldn't recommend leaving that repo active or using it to upgrade anything else, but it does have the latest version of Ktorrent.

I'm frustrated that the Ubuntu repos don't have the latest Ktorrent version. Version 3.1.5 was released on Nov 15 -- 2 months ago -- and fixes "one nasty crash caused by a Qt bug." If a "nasty" bug isn't a high enough priority, what exactly qualifies to be added to the Ubuntu repositories?

---

### Post by sickanimations on 2009-02-10
I agree completely. Tonight I've spent about 3 hours just trying to compile the latest rc of ktorrent. I had to download and install about 10 libraries - probably 200MB of data. Lucky I'm not on dialup or slow ADSL.

... Although this is the first time I have used cmake.

Does anybody know how/if such packages can be installed automatically?

All I want is a reliable BitTorrent client that has robust support for RSS :( I miss you, uTorrent...

---

### Post by utkjamie on 2009-02-10
> Does anybody know how/if such packages can be installed automatically?Yes. See my previous post. Use the Debian Sid repository to install/upgrade Ktorrent and then disable that repository after you've installed the latest version of Ktorrent. Don't use it to upgrade or install anything else.

---

### Post by _salem_ on 2009-05-05
I downloaded the .deb from the link above, but when i try and install it it gives the error "Error: dependency is not satisfiable: ktorrent-data"

any clues?

I was installing by just double-clicking on the .deb and letting the package installer launch.

---

