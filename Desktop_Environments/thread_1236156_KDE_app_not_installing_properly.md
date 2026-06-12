---
title: "KDE app not installing properly"
date: 2009-08-10
forum: Desktop Environments
---

### Post by addiebk on 2009-08-10
I'm trying to install the application KMuddy, [http://www.kmuddy.com/index.php/Main_Page](http://www.kmuddy.com/index.php/Main_Page), and I just can't seem to get it to work.

I tried the binary for xUbuntu 9.04, and it seemed to install properly, but when I run the command for the program, I am presented with the error: > kmuddy: error while loading shared libraries: libmxp.so.0: cannot open shared object file: No such file or directory

When I try to compile from source, I first untar (tar xzf kmuddy-1.0.tar.gz) the file, then I start having problems.  Following the directions on the website, I enter the command cmake, which seems to work, then make install.  The error:  > make: *** No rule to make target `install'.  Stop.  This error also appears when I run sudo make install.

I tried running ./configure, which gives the error:
> -- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/addie/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:5 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!

I know that Gnome/KDE crossover is not perfect, but I've read accounts of this particular program working in the Gnome environment.  Is there any way that I can get this working?  It would be a huge help.

---

