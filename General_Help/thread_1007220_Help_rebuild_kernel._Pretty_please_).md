---
title: "Help rebuild kernel. Pretty please :)"
date: 2008-12-10
forum: General Help
---

### Post by roccivic on 2008-12-10
I have VMWare server installed, recently installed a few updates through apt including GCC and new kernel. Now VMWare won't run and says that it needs to recompile some modules. Unfortunately VMware's modules won't build due to a GCC incompatibility or something along these lines anyway....

```
Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] y

```


So if someone could tell me how to rebuild my kernel using GCC 4.2.4 or point me in the right direction if I don't need to mess with the kernel that would be just great!

Thank you for your time.

Rouslan.

---

### Post by linux_tech on 2008-12-10
Try setting the gcc version, see this link for how to do this-
[http://ubuntuforums.org/showthread.php?t=65638](http://ubuntuforums.org/showthread.php?t=65638)
but use  apt-get install gcc-4.2.3

---

### Post by roccivic on 2008-12-10
> **linux_tech said:**
> but use  apt-get install gcc-4.2.3

Doesn't seem to exist....  :(

```
roccivic@roccivic-office-pc:~$ sudo apt-get install gcc-4.2.3
[sudo] password for roccivic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc-4.2.3
roccivic@roccivic-office-pc:~$ apt-cache search gcc
cpp-4.1 - The GNU C preprocessor
gcc-4.1 - The GNU C compiler
gcc-4.1-base - The GNU Compiler Collection (base package)
gcc-4.1-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-4.1-multilib - The GNU C compiler (multilib files)
gcc-4.1-source - Source of the GNU Compiler Collection
acovea - analysis of compiler options via evolutionary algorithms
cableswig - Generate wrappers for Python and Tcl from C++ code
colorgcc - Colorizer for GCC warning/error messages
cpphs - Simplified cpp-a-like preprocessor for Haskell
cstream - general-purpose stream-handling tool similar to dd
cxref - Generates latex and HTML documentation for C programs
gcc-4.1-locales - The GNU C compiler (native language support files)
gcc-avr - The GNU C compiler (cross compiler for avr)
gcc-h8300-hms - The GNU C compiler (cross compiler for h8300-hitachi-coff)
gcc-m68hc1x - GNU C compiler for the Motorola 68HC11/12 processors
gcc-snapshot - A SNAPSHOT of the GNU Compiler Collection
gccxml - XML output extension to GCC
gcj-4.1 - The GNU compiler for Java(TM)
gcj-4.1-base - The GNU Compiler Collection (gcj base package)
gdc-4.1 - The D compiler
gfortran-4.1 - The GNU Fortran 95 compiler
gfortran-4.1-multilib - The GNU Fortran 95 compiler (multilib files)
ggcov - Graphical tool for displaying gcov test coverage data
ghdl - VHDL compiler/simulator using GCC technology
gnat-4.1 - The GNU Ada compiler
gnat-4.1-base - The GNU Compiler Collection (gnat base package)
gobjc++-4.1 - The GNU Objective-C++ compiler
gobjc++-4.1-multilib - The GNU Objective-C++ compiler (multilib files)
gobjc-4.1 - The GNU Objective-C compiler
gobjc-4.1-multilib - The GNU Objective-C compiler (multilib files)
gpc-4.1 - The GNU Pascal compiler
gpc-4.1-doc - Documentation for the GNU Pascal compiler (gpc)
hardening-wrapper - experimental compiler wrapper to enable security hardening flags
libacovea-5.1-5 - library for analyzing compiler options via evolutionary algorithms
libacovea-dev - library for analyzing compiler options via evolutionary algorithms
libeigen-dev - lightweight C++ template library for linear algebra
libgcj7-1 - Java runtime library for use with gcj
libgcj7-dev - Java development headers and static library for use with gcj
libgcj7-jar - Java runtime library for use with gcj (jar files)
libmudflap0-dev - GCC mudflap support libraries (development files)
llvm - Low-Level Virtual Machine (LLVM) compiler for C/C++
mcpp - Alternative C/C++ preprocessor
motor - C/C++/Java Integrated Development Environment
motor-common - C/C++/Java Integrated Development Environment
motor-fribidi - C/C++/Java Integrated Development Environment
open-cobol - COBOL compiler
pentium-builder - force pentium optimized compilation
pilrc - PalmOS resource compiler and editor
pilrcui - graphical viewer for PalmOS resource files
pocketpc-gcc - The GNU C compiler for Pocket PC
ppu-gcc - PPU C compiler
ratfor - Rational Fortran preprocessor for Fortran 77
spu-gcc - SPU cross-compiler (preprocessor and C compiler)
stalin - An extremely aggressive Scheme compiler
sysinfo - Simple GTK program that shows some UNIX/Linux system information
tcc - the smallest ANSI C compiler
treelang-4.1 - The GNU Treelang compiler
uisp - Micro In-System Programmer for Atmel's AVR MCUs
cpp - The GNU C preprocessor (cpp)
cpp-4.2 - The GNU C preprocessor
dpkg-dev - package building tools for Debian
gcc - The GNU C compiler
gcc-4.2 - The GNU C compiler
gcc-4.2-base - The GNU Compiler Collection (base package)
gcc-4.2-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-4.2-locales - The GNU C compiler (native language support files)
gcc-4.2-multilib - The GNU C compiler (multilib files)
gcc-4.2-source - Source of the GNU Compiler Collection
gcc-doc - Documentation for the GNU C compilers (gcc, gobjc, g++)
gcc-multilib - The GNU C compiler (multilib files)
gcj - The GNU Java compiler
gcj-4.2 - The GNU compiler for Java(TM)
gcj-4.2-base - The GNU Compiler Collection (gcj base package)
gfortran - The GNU Fortran 95 compiler
gfortran-4.2 - The GNU Fortran 95 compiler
gobjc - The GNU Objective-C compiler
gobjc-4.2 - The GNU Objective-C compiler
lib64gcc1 - GCC support library (64bit)
lib64gcc1-dbg - GCC support library (debug symbols)
lib64gomp1 - GCC OpenMP (GOMP) support library (64bit)
lib64gomp1-dbg - GCC OpenMP (GOMP) support library (64bit debug symbols)
libgcc1 - GCC support library
libgcc1-dbg - GCC support library (debug symbols)
libgcj8-1 - Java runtime library for use with gcj
libgcj8-dev - Java development headers for use with gcj
libgcj8-jar - Java runtime library for use with gcj (jar files)
libgomp1 - GCC OpenMP (GOMP) support library
libgomp1-dbg - GCC OpenMP (GOMP) support library (debug symbols)
cpp-3.3 - The GNU C preprocessor
cpp-3.4 - The GNU C preprocessor
g++-3.4 - The GNU C++ compiler
g77 - The GNU Fortran 77 compiler
g77-3.4 - The GNU Fortran 77 compiler
gcc-3.3 - The GNU C compiler
gcc-3.3-base - The GNU Compiler Collection (base package)
gcc-3.3-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-3.4 - The GNU C compiler
gcc-3.4-base - The GNU Compiler Collection (base package)
gcc-3.4-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gdc-4.2 - The D compiler
gfortran-4.2-multilib - The GNU Fortran 95 compiler (multilib files)
gfortran-multilib - The GNU Fortran 95 compiler (multilib files)
gnat-4.2 - The GNU Ada compiler
gnat-4.2-base - The GNU Compiler Collection (gnat base package)
gobjc++ - The GNU Objective-C++ compiler
gobjc++-4.2 - The GNU Objective-C++ compiler
gobjc++-4.2-multilib - The GNU Objective-C++ compiler (multilib files)
gobjc++-multilib - The GNU Objective-C++ compiler (multilib files)
gobjc-4.2-multilib - The GNU Objective-C compiler (multilib files)
gobjc-multilib - The GNU Objective-C compiler (multilib files)
gpc - The GNU Pascal compiler
gpc-2.1-3.4 - The GNU Pascal compiler
gpc-2.1-3.4-doc - Documentation for the GNU Pascal compiler (gpc)
lib64mudflap0 - GCC mudflap shared support libraries (64bit)
lib64mudflap0-dbg - GCC mudflap shared support libraries (64 bit debug symbols)
libmudflap0 - GCC mudflap shared support libraries
libmudflap0-4.2-dev - GCC mudflap support libraries (development files)
libmudflap0-dbg - GCC mudflap shared support libraries (debug symbols)
treelang-4.2 - The GNU Treelang compiler
roccivic@roccivic-office-pc:~$ 
```

---

### Post by linux_tech on 2008-12-10
You may be able to use a patch found here-
[http://lenrek.wordpress.com/2008/08/31/vmware-server-107-with-linux-kernel-2626x/](http://lenrek.wordpress.com/2008/08/31/vmware-server-107-with-linux-kernel-2626x/)

To get past E: Couldn't find package gcc-4.2.3
remove_proc_entry may help-
[http://ubuntuforums.org/showthread.php?t=999090](http://ubuntuforums.org/showthread.php?t=999090)

---

