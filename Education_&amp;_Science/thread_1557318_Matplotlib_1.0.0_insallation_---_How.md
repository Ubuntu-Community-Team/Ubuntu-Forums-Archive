---
title: "Matplotlib 1.0.0 insallation --- How?"
date: 2010-08-20
forum: Education &amp; Science
---

### Post by virsto on 2010-08-20
I have an Ubuntu 10.04 64-bit system.

I have downloaded the latest release of NumPy (numpy-1.5.0b2.tar.gz), extracted it to 

  home/Downloads/numpy-1.5.0b2/

and then executed in Python 2.6

  setup.py  install

Unfortunately, this does not install numpy :(

I have attached the output produced when I executed the above. This listing shows that there are many problems/errors in the attempted installation.

Help on this would be appreciated --- What next?

---

### Post by gunksta on 2010-08-20
You're missing many of numpy's dependencies.
```
apt-cache show python-numpy
```Should show you the following.

*Depends: python (<< 2.7), python (>= 2.6), python-central (>= 0.6.11), libblas3gf | libblas.so.3gf | libatlas3gf-base, libc6 (>= 2.11), libgcc1 (>= 1:4.1.1), libgfortran3 (>= 4.3), liblapack3gf | liblapack.so.3gf | libatlas3gf-base*

You certainly have python, etc installed but you are clearly missing some of the blas dependencies and what not. I would try installing the missing dependencies and then try again. Of course, if the newer version of numpy has additional / newer dependencies, this still won't work until those problems are addressed as well.

When you think about how complicated it is to update even a single library, it really makes you appreciate the work done by distros like Ubuntu, Fedora, Slackware, etc.

BTW - I do not recommend installing the newer version of numpy as a system-wide component. Install it locally. I maintain ~/bin and ~/lib for libraries and programs that I want to update for use in my own personal work/scripts. If a program tries to use the system-wide version of numpy it may or may not work, depending on the interaction between that application and the newer library. Python libs are often safer to upgrade system-wide than C libs, but I would still install it locally, so you don't risk messing stuff up.

---

