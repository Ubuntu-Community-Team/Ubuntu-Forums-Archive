---
title: "installed gcc,  got weird compile errors (C++)"
date: 2009-04-02
forum: General Help
---

### Post by agnes on 2009-04-02
Hello everyone,

I'm now running Ubuntu (8.10) for only a few days (no prev. Linux experience).
One of the first things I wanted to get working was a c/c++ compiler.

I have some files I used to compile via ssh on my school account, there they have gcc (also for c++) installed. 
They have Fedora as OS.
What worked, there, was just this command:

[FONT="Courier New"]c++ file.cpp -o file[/FONT]

I have (on my own PC) gcc (version 4.2 and 4.3) via Synaptic, and I have g++ (also version 4.2 and 4.3), and, I've installed the build-essential package (after I got gcc, I believe).

However, the same code that compiled fine on my school account/PC does not compile fine here.
No matter if I use "[FONT="Courier New"]c++ file.cpp -o file[/FONT]" or "[FONT="Courier New"]g++ file.cpp -o file[/FONT]" or "[FONT="Courier New"]gcc file.cpp -o file[/FONT]".

This is the error I get (when calling c++):
-------------------------------------------------
[FONT="Courier New"]nntest01.cpp: In function &#8216;void run_sample(Matrix, Matrix&, Matrix&, double&, int, bool, int&)&#8217;:
nntest01.cpp:212: error: &#8216;INT_MIN&#8217; was not declared in this scope
nntest01.cpp: In function &#8216;void train(int*, Matrix, Matrix&, Matrix&)&#8217;:
nntest01.cpp:269: error: &#8216;INT_MAX&#8217; was not declared in this scope
matrix.h: In constructor &#8216;math::matrix<T>::base_mat::base_mat(size_t, size_t, T**) [with T = double]&#8217;:
matrix.h:326:   instantiated from &#8216;math::matrix<T>::matrix(size_t, size_t) [with T = double]&#8217;
nntest01.cpp:344:   instantiated from here
matrix.h:298: error: &#8216;memcpy&#8217; was not declared in this scope[/FONT]
--------------------------------------------------

So it can't handle INT_MIN and INT_MAX, and it has problems with matrix.h, which is a matrix class library I downloaded (and should be compatible with GNU C++ 2.xx according to the website of the authors).

Does anyone have any idea why this is the case? 
(I have an AMD X2 64-bits processor, by the way. But as far as I know, the school-PC's also run on an AMD 64-bits.)

This is what I get on my own PC when I do 'man -k gcc':
--------------------------------------------
[FONT="Courier New"]$ man -k gcc	
	
builder-cc (1)       - gcc wrapper to facilitate pentium-optimizations
c89-gcc (1)          - ANSI (1989) C compiler
c99-gcc (1)          - ANSI (1999) C compiler
gcc (1)              - GNU project C and C++ compiler
gcc-4.2 (1)          - GNU project C and C++ compiler
gcc-4.3 (1)          - GNU project C and C++ compiler
x86_64-linux-gnu-gcc (1) - GNU project C and C++ compiler
x86_64-linux-gnu-gcc-4.2 (1) - GNU project C and C++ compiler
x86_64-linux-gnu-gcc-4.3 (1) - GNU project C and C++ compiler[/FONT]
--------------------------------------------

And this is what I get when I do 'man -k gcc'  on the school-PC:
--------------------------------------------
[FONT="Courier New"]$ man -k gcc

compat-gcc-34       (rpm) - Compatibility GNU Compiler Collection
compat-gcc-34-g77   (rpm) - Fortran 77 support for compatibility compiler
gcc                  (1)  - GNU project C and C++ compiler
gcc                 (rpm) - Various compilers (C, C++, Objective-C, Java, ...)
gcc [g++]            (1)  - GNU project C and C++ compiler
gcc-c++             (rpm) - C++ support for GCC
gcc-gfortran        (rpm) - Fortran 95 support
gcc-java            (rpm) - Java support for GCC
gccmakedep           (1x)  - create dependencies in makefiles using 'gcc -M'
libgcc              (rpm) - GCC version 4.1 shared support library
libgcj              (rpm) - Java runtime library for gcc
libgcj-devel        (rpm) - Libraries for Java development using GCC
libgcj-src          (rpm) - Java library sources from GCC4 preview
libgomp             (rpm) - GCC OpenMP 2.5 shared support library[/FONT]
--------------------------------------------

 Thanks in advance.

---

### Post by snova on 2009-04-02
> ```

nntest01.cpp: In function &#8216;void run_sample(Matrix, Matrix&, Matrix&, double&, int, bool, int&)&#8217;:
nntest01.cpp:212: error: &#8216;INT_MIN&#8217; was not declared in this scope
nntest01.cpp: In function &#8216;void train(int*, Matrix, Matrix&, Matrix&)&#8217;:
nntest01.cpp:269: error: &#8216;INT_MAX&#8217; was not declared in this scope
matrix.h: In constructor &#8216;math::matrix<T>::base_mat::base_mat(size_t, size_t, T**) [with T = double]&#8217;:
matrix.h:326: instantiated from &#8216;math::matrix<T>::matrix(size_t, size_t) [with T = double]&#8217;
nntest01.cpp:344: instantiated from here
matrix.h:298: error: &#8216;memcpy&#8217; was not declared in this scope

```

matrix.h appears to be using the memcpy() function, so at the top of that file, add this line:

```
#include <string.h>
```

And nntest01.cpp is using INT_MAX and INT_MIN, so:

```
#include <limits.h>
```

---

### Post by agnes on 2009-04-03
Thanks, it worked. :)

Do you perhaps also know why I don't have to include this when compiling on the school PC? 
Is it a certain library package they use that automatically takes care for these things?

---

### Post by ibuclaw on 2009-04-03
Firstly, if you are compiling C++ code, always use either **g++** or **c++**.

Secondly, you could replace the headers you put in for this:
```

#include <cstring>
#include <climits>

```

[QUOTE=agnes]
Do you perhaps also know why I don't have to include this when compiling on the school PC? 
[/QUOTE]
Thirdly, that would depend mostly on what IDE, Compiler and Operating System you use at school.
Different implementations will act differently...

Lastly, here is a good reference site if you are having problems figuring out what is declared where: [http://www.cplusplus.com/reference/clibrary/](http://www.cplusplus.com/reference/clibrary/)

Regards
Iain

---

