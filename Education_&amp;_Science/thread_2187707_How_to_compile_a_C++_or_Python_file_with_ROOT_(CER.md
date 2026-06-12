---
title: "How to compile a C++ or Python file with ROOT (CERN) libraries?"
date: 2013-11-13
forum: Education &amp; Science
---

### Post by GHh3LrM on 2013-11-13
Hello to everyone,
I am new to the field and I would need help with a simple problem. I'd like to compile files written either in C++ or in Python that include Cern ROOT libraries. For example I'd like to write a program that produces some data which are manipulated with simple algorythms in Python or in C++ and then I'd like to produce a plot of this data with ROOT. The fact is, how do I tell the compiler to go look for ROOT libraries in the right place when I call them? For example, if I write a file in C++ stating:

include "TFile.h"

it tells me that such file doesn't exist, because I guess it looks for it in the same place where there are standard c++ libraries, whereas I've installed ROOT in another directory.

Same problem with Python.

I am currently using gcc as C++ compiler and Ipython as Python compiler (just installed, so last versions).

Any help would be great!

---

### Post by steeldriver on 2013-11-13
From **man g++**

```

       -Idir
           Add the directory dir to the head of the list of directories to be
           searched for header files.  

```
and
```

       -l library
           Search the library named library when linking. 

```
and
```

       -Ldir
           Add directory dir to the list of directories to be searched for -l.

```

I am not familiar with Ipython - sorry

---

