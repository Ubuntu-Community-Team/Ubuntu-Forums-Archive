---
title: "Boson help..."
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by ardvark71 on 2006-11-07
Hi Everyone...

Please forgive me if this a little long winded but I wanted to give you much detail as possible concerning my problem...

I'm trying to install the latest version of boson (0.13) on my copy of Breezy and I "think" I've taken care of all the needed dependencies.....hopefully.

OK...I've downloaded the "big" file which includes everything...source, data, music, etc. and have went to the developers web site to get the specific install instructions, which are:

$ tar xjvf boson-all-0.13.tar.bz2
$ cd boson-all-0.13
$ mkdir build
$ cd build
$ cmake ..
$ make
$ su
# make install

Looks easy enough, considering it's command line.

Everthing goes fine until I get to cmake, when after running that command I receive the following message:

-- Check for working C compiler: gcc -- works
-- Check for working CXX compiler: c++ -- works
CMake Error: Error in cmake code at
/home/thecount/boson-all-0.13/CMakeLists.txt:1:
Unknown CMake command "project".
CMake Error: Error in cmake code at
/home/thecount/boson-all-0.13/CMakeLists.txt:3:
Unknown CMake command "add_subdirectory".
CMake Error: Error in cmake code at
/home/thecount/boson-all-0.13/CMakeLists.txt:4:
Unknown CMake command "add_subdirectory".
CMake Error: Error in cmake code at
/home/thecount/boson-all-0.13/CMakeLists.txt:5:
Unknown CMake command "add_subdirectory".
-- Configuring done

This doesn't look very good but I decide to press on anyway and go to "make" which, in turn, gives this message:

make: *** No targets specified and no makefile found.  Stop.

I'm afraid I'm at a loss to understand what's going on:confused: As corny as it sounds, I've recently just migrated to Linux full time and I'm trying to grasp the "language" used in the terminal and I admit it's been a trying experience.

I looked around at both Ubuntu's forums and the help pages at the developer's site and disn't see anything pertaining to this problem.

Does anyone have any ideas?

Thanks! :KS

---

### Post by Joe_CoT on 2006-11-08
Did you use the instructions in the INSTALL file?
```

Currently you need to do:
export QTDIR=/path/to/qt
export KDEDIR=`kde-config --prefix`
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/where/to/install/to ..
make
```

do you have the newest version of cmake?

I'm compiling it right now.

---

### Post by ardvark71 on 2006-11-08
Hi Joe...

cmake is version 2.0.5-1build1, although I don't know if that is the most current version or not. I will have to look it up...

But the extra install instructions is what I obviously missed...thank you!
Does the game work well for you?

---

### Post by Joe_CoT on 2006-11-10
> Does the game work well for you?

Actually, when loading a map, if goes into an infinite loop of errors ;) but using the instructions, it certainly built fine! :D

---

