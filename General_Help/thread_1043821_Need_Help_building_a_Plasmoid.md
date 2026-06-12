---
title: "Need Help building a Plasmoid"
date: 2009-01-18
forum: General Help
---

### Post by Dieseler on 2009-01-18
Trying to follow directions from kdelook.org to build a weather plasmoid.
I installed cmake then the next job was 

> cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` 


I'm getting the error

> -- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

I know I'm missing a library but not sure which one to install.
Any would be great,
Thanks

---

### Post by snova on 2009-01-18
Install the 'build-essential' package, and also 'libplasma-dev'.

---

### Post by Dieseler on 2009-01-19
Thanks, I finally got it sorted.

---

