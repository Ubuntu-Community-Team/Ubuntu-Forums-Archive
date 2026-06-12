---
title: "Install Petsc/Tao C++"
date: 2009-06-14
forum: General Help
---

### Post by lidengdeng on 2009-06-14
Hi, I met a problem when I tries to run an open-source.

In the readme file, it says "You'll also need the Boost C++ and the Petsc/Tao C++ libraries in order to ...".

But I don't know how to install Petsc/Tao C++ libraries on Ubuntu8.04. It fails to comply the open-source and produces the following errors:

tao-optimizer.h: At global scope:
tao-optimizer.h:93: error: 'PetscReal' has not been declared
tao-optimizer.h: In constructor 'tao_environment::tao_environment(int&, char**&, const char*)':
tao-optimizer.h:74: error: 'PetscInitialize' was not declared in this scope
tao-optimizer.h:75: error: 'TaoInitialize' was not declared in this scope
......
......


So how to install Petsc/Tao on Ubuntu? Thanks

---

