---
title: "How to install gromacs 5.x in ubuntu trusty 14.04"
date: 2015-12-04
forum: Education &amp; Science
---

### Post by Claus7 on 2015-12-04
Hello,

here I will describe the steps I followed in order to install the latest version of gromacs in ubuntu Trusty:

1) install the cmake package by going here: [https://launchpad.net/~george-edison55/+archive/ubuntu/cmake-3.x](https://launchpad.net/~george-edison55/+archive/ubuntu/cmake-3.x)
and which will add a repository which will install the latest version of cmake

In order to test that it was installed successfully type:
```
cmake -version

```
Then, open synaptic and install:

2) libxml2-dev

3) libfftw3-single3 along with bin and dev files

4) download the latest gromacs package

5) untar it and follow these guidelines to test a possible installation:

> $ tar xfz gromacs-5.x.x.tgz
$ cd gromacs-5.x.x
$ mkdir build-gromacs
$ cd build-gromacs
$ cmake ..

every time you would like to test if you have installed a dependency for gromacs do not forget to type:
```

rm CMakeCache.txt
```
which will allow you to remove the old file so as to recheck for a new possible installation.

In other words step 5 will show you if you are missing any (more) libraries that need to be installed.

6) Then follow gromacs installation sequence of commands:

i) enter, if not already, the gromacs folder:
```
cd gromacs-5.x.x
```
ii) create empty folder build:
```
mkdir build
```
iii) change to build directory:
```
cd build
```
iv) use cmake by denoting that you will use the proposed gromacs library (if you do not want, you can omit the corresponding argument): 
```
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
```
v) compile gromacs
```
make
```
vi) check the process
```
make check
```
vii) install gromacs
```
sudo make install
```
viii) make the current terminal to understand that you will use the new version of gromacs (if you have already installed the previous version of gromacs via synaptic):
```
source /usr/local/gromacs/bin/GMXRC
```

Done!

From step 6iv and on you will have to wait a little while until the process is finished. You can check if everything is ok by typing:
```
gmx grompp -h 
```

on the same terminal that you typed all the previous commands (especially the very last one, which you should type very time you wish to use the new version of gromacs unless you make a link).

If you are not happy with the installation, then go back to the folder you did the installation and type:
```
sudo make uninstall
```

Hope it helps,
Regards!

---

### Post by Portaro on 2015-12-04
:p Hey thanks for share and help other users.

Many thanks for this contribution. :D

---

