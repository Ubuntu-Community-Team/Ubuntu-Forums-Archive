---
title: "Configure error when trying to install Super Tux Kart"
date: 2006-08-08
forum: Desktop Environments
---

### Post by FNM on 2006-08-08
I'm trying to compile Super Tux Kart since there are no binary packages for it, and I'm getting stuck on this error.

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether we should use SDL... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.4... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
checking for IMG_Load in -lSDL_image... no
configure: error: SDL_image library required
```

Any ideas?

---

### Post by louis_nichols on 2006-08-08
yes you need to install a package called something-SDL-something-dev. This the general rule when such errors show up during configure. The package in question is probably libsdl1.2-dev.

---

### Post by FNM on 2006-08-08
Thanks for the help, but I'm getting a dependency error when I attemp to install libsdl1.2-dev

```
libsdl1.2-dev:
 Depends: libartsc0-dev but it is not going to be installed
```

:sad:

---

### Post by Ramses de Norre on 2006-08-08
libartsc0-dev is available in [dapper main](http://packages.ubuntu.com/dapper/libdevel/libartsc0-dev)..
What's the output of sudo aptitude install libartsc0-dev?

---

### Post by FNM on 2006-08-08
I managed to get the packages installed, but I'm still getting stuck on that configuration error.

```
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libglib2.0-dev
The following NEW packages will be installed:
  libartsc0-dev
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 519kB of archives. After unpacking 2114kB will be used.
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libglib2.0-0 [2.10.3-0ubuntu1 (now) -> 2.10.2-1ubuntu3 (dapper)]
libglib2.0-data [2.10.3-0ubuntu1 (now) -> 2.10.2-1ubuntu3 (dapper)]

Score is -130

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libglib2.0-dev
The following packages will be DOWNGRADED:
  libglib2.0-0 libglib2.0-data
The following NEW packages will be installed:
  libartsc0-dev libglib2.0-dev
```

---

### Post by Ramses de Norre on 2006-08-08
I don't know the exact package you need but this might help:
```
sudo aptitude update && sudoa aptidue install auto-apt
sudo auto-apt update
sudo auto-apt updatedb
sudo auto-apt update-local
sudo auto-apt run ./configure
./configure
```
auto-apt will ask you to install all needed packages, just choose yes. The update commands can take some time.

---

### Post by FNM on 2006-08-08
Thanks for the help, but I'm afraid I'll never get this game installed. Using the method you described just unleashed a whole bunch of seg faults, and broken dependencies.:mad:

---

