---
title: "c man pages?"
date: 2005-01-07
forum: Desktop Environments
---

### Post by earobinson on 2005-01-07
is ubuntu missing the c man pages?

in fedora i was able to type "man string.h" and get the string man page how do i do this in ununtu

---

### Post by az on 2005-01-07
sudo apt-get install build-essential gcc-3.3-doc c-cpp-reference


apt-cache search gcc|grep doc

---

### Post by earobinson on 2005-01-08
[QUOTE=azz]sudo apt-get install build-essential gcc-3.3-doc c-cpp-reference


apt-cache search gcc|grep doc[/QUOTE]

I did that and it still dont work
```
earobinson@user78-213:~ $ sudo apt-get install build-essential gcc-3.3-doc c-cpp-reference
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
build-essential is already the newest version.
Suggested packages:
  kdevelop
The following NEW packages will be installed:
  c-cpp-reference gcc-3.3-doc
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2175kB of archives.
After unpacking 9409kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com warty/universe c-cpp-reference 2.0.2-2 [946kB]
Get:2 http://archive.ubuntu.com warty/main gcc-3.3-doc 1:3.3.4-9ubuntu5 [1229kB]Fetched 2175kB in 7s (291kB/s)

Preconfiguring packages ...
Selecting previously deselected package c-cpp-reference.
(Reading database ... 71087 files and directories currently installed.)
Unpacking c-cpp-reference (from .../c-cpp-reference_2.0.2-2_all.deb) ...
Selecting previously deselected package gcc-3.3-doc.
Unpacking gcc-3.3-doc (from .../gcc-3.3-doc_1%3a3.3.4-9ubuntu5_all.deb) ...
Setting up c-cpp-reference (2.0.2-2) ...

Setting up gcc-3.3-doc (3.3.4-9ubuntu5) ...

earobinson@user78-213:~ $ apt-cache search gcc|grep doc
gcc-3.3-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-doc - Documentation for the GNU C compilers (gcc, gobjc, g++)
aegis-doc - Documentation for aegis
aegis3-doc - Documentation for aegis3
cpp-2.95-doc - Documentation for the GNU C preprocessor (cpp)
cxref - Generates latex and HTML documentation for C programs
g77-2.95-doc - Documentation for the GNU Fortran compiler (g77)
gcc-2.95-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-3.2-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-3.4-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc272-docs - Documentation for the gcc compiler (gcc272).
gpc-2.1-3.3-doc - Documentation for the GNU Pascal compiler (gpc)
gpc-2.1-3.4-doc - Documentation for the GNU Pascal compiler (gpc)
gpc-2.95-doc - Documentation for the GNU Pascal compiler (gpc)
earobinson@user78-213:~ $ man string.h
No manual entry for string.h
earobinson@user78-213:~ $ man strcpy
No manual entry for strcpy
earobinson@user78-213:~ $ sudo man string.h

```

---

### Post by earobinson on 2005-01-12
[QUOTE=azz]sudo apt-get install build-essential gcc-3.3-doc c-cpp-reference


apt-cache search gcc|grep doc[/QUOTE]

I did that and it still dont work
```
earobinson@user78-213:~ $ sudo apt-get install build-essential gcc-3.3-doc c-cpp-reference
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
build-essential is already the newest version.
Suggested packages:
  kdevelop
The following NEW packages will be installed:
  c-cpp-reference gcc-3.3-doc
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2175kB of archives.
After unpacking 9409kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com warty/universe c-cpp-reference 2.0.2-2 [946kB]
Get:2 http://archive.ubuntu.com warty/main gcc-3.3-doc 1:3.3.4-9ubuntu5 [1229kB]Fetched 2175kB in 7s (291kB/s)

Preconfiguring packages ...
Selecting previously deselected package c-cpp-reference.
(Reading database ... 71087 files and directories currently installed.)
Unpacking c-cpp-reference (from .../c-cpp-reference_2.0.2-2_all.deb) ...
Selecting previously deselected package gcc-3.3-doc.
Unpacking gcc-3.3-doc (from .../gcc-3.3-doc_1%3a3.3.4-9ubuntu5_all.deb) ...
Setting up c-cpp-reference (2.0.2-2) ...

Setting up gcc-3.3-doc (3.3.4-9ubuntu5) ...

earobinson@user78-213:~ $ apt-cache search gcc|grep doc
gcc-3.3-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-doc - Documentation for the GNU C compilers (gcc, gobjc, g++)
aegis-doc - Documentation for aegis
aegis3-doc - Documentation for aegis3
cpp-2.95-doc - Documentation for the GNU C preprocessor (cpp)
cxref - Generates latex and HTML documentation for C programs
g77-2.95-doc - Documentation for the GNU Fortran compiler (g77)
gcc-2.95-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-3.2-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc-3.4-doc - Documentation for the GNU compilers (gcc, gobjc, g++)
gcc272-docs - Documentation for the gcc compiler (gcc272).
gpc-2.1-3.3-doc - Documentation for the GNU Pascal compiler (gpc)
gpc-2.1-3.4-doc - Documentation for the GNU Pascal compiler (gpc)
gpc-2.95-doc - Documentation for the GNU Pascal compiler (gpc)
earobinson@user78-213:~ $ man string.h
No manual entry for string.h
earobinson@user78-213:~ $ man strcpy
No manual entry for strcpy
earobinson@user78-213:~ $ sudo man string.h

```

---

### Post by randy on 2005-01-12
The packages that you need are
manpages-posix and
manpages-posix-dev

---

### Post by KoS on 2005-01-13
[QUOTE=randy]The packages that you need are
manpages-posix and
manpages-posix-dev[/QUOTE]

In fact in ubuntu you need:
*manpages* **and**
*manpages-dev*

---

### Post by earobinson on 2005-01-13
[QUOTE=KoS]In fact in ubuntu you need:
*manpages* **and**
*manpages-dev*[/QUOTE]
 instaled them and still
```
earobinson@user78-213:~ $ man string.h
No manual entry for string.h
```

---

### Post by shrekkie on 2005-03-03
so is someone able to access the manpages for c functions etc? Do the above procedures work? Please help out a n00b to Ubuntu here :) I mainly use ubuntu for C programming and if I can't access any of the manpages for c, I would be crippled :(

---

### Post by silviutp on 2007-11-11
manpages-posix-dev - for c headers
manpages-dev - for c functions

---

### Post by briguyd on 2008-02-19
> **silviutp said:**
> manpages-posix-dev - for c headers
manpages-dev - for c functions

Thanks, that worked for me.

---

