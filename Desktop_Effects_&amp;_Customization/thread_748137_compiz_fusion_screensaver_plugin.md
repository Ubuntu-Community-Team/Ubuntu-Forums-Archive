---
title: "compiz fusion screensaver plugin"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by lilalmond on 2008-04-07
Hey

I tried to install the screensaver plugin following the instruction from the thread "how to 13 plugins for compiz in gutsy", and i ran into some errors.

```
amandine@amandine:~$ wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f'
--15:42:33--  http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f
           => `/tmp/screensaver.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [  <=>                                ] 14 550        61.36K/s             

15:42:34 (61.26 KB/s) - `/tmp/screensaver.tar.gz' saved [14550]

amandine@amandine:~$ tar -xf '/tmp/screensaver.tar.gz' -C ~/compiz/
amandine@amandine:~$ cd ~/compiz/screensaver
amandine@amandine:~/compiz/screensaver$ make
compiling : matrix.cpp -> build/matrix.loPackage xscrnsaver was not found in the pkg-config search path.
Perhaps you should add the directory containing `xscrnsaver.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xscrnsaver' found
In file included from matrix.cpp:1:
matrix.h:5:20: error: compiz.h: No such file or directory
vector.h:34: error: 'CompScreen' has not been declared
vector.h:43: error: 'CompScreen' has not been declared
vector.h: In member function 'Vector Vector::toScreenSpace(int*) const':
vector.h:37: error: request for member 'width' in '* s', which is of non-class type 'int'
vector.h:38: error: request for member 'height' in '* s', which is of non-class type 'int'
vector.h: In member function 'Vector Vector::toCoordsSpace(int*) const':
vector.h:46: error: request for member 'width' in '* s', which is of non-class type 'int'
vector.h:47: error: request for member 'height' in '* s', which is of non-class type 'int'
matrix.h: At global scope:
matrix.h:15: error: expected ',' or '...' before '*' token
matrix.h:15: error: ISO C++ forbids declaration of 'CompTransform' with no type
matrix.h: In constructor 'Matrix::Matrix(int)':
matrix.h:15: error: 'mat' was not declared in this scope
matrix.h: In member function 'Matrix& Matrix::rotate(float, float, float, float)':
matrix.h:30: error: 'CompTransform' was not declared in this scope
matrix.h:30: error: expected primary-expression before ')' token
matrix.h:30: error: 'matrixRotate' was not declared in this scope
matrix.h: In member function 'Matrix& Matrix::scale(float, float, float)':
matrix.h:38: error: 'CompTransform' was not declared in this scope
matrix.h:38: error: expected primary-expression before ')' token
matrix.h:38: error: 'matrixScale' was not declared in this scope
matrix.h: In member function 'Matrix& Matrix::translate(float, float, float)':
matrix.h:46: error: 'CompTransform' was not declared in this scope
matrix.h:46: error: expected primary-expression before ')' token
matrix.h:46: error: 'matrixTranslate' was not declared in this scope
make: *** [build/matrix.lo] Error 1
amandine@amandine:~/compiz/screensaver$ 
```

I already installed other plugins like 3D Windows, snow,snowglobe,fireflies and got them to work.
Can anyone help me out?

---

### Post by jryprt on 2008-04-07
Go to your home folder & open compiz folder & delete screensaver folder & try to install again . I just installed it again with no errors.

---

### Post by lilalmond on 2008-04-07
> **jryprt said:**
> Go to your home folder & open compiz folder & delete screensaver folder & try to install again . I just installed it again with no errors.

I deleted the screensaver folder in the compiz folder and reinstalled the plugin but i still have the same errors...
I dont understand why im having trouble installing this plugin, because i already installed other plugins without any problems.
Thanx for your suggestion anyway

---

### Post by lilalmond on 2008-04-07
Just wanted to point out that its when i run the command "make" that i get this output:

```
amandine@amandine:~/compiz/screensaver$ make
compiling : matrix.cpp -> build/matrix.loPackage xscrnsaver was not found in the pkg-config search path.
Perhaps you should add the directory containing `xscrnsaver.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xscrnsaver' found
In file included from matrix.cpp:1:
matrix.h:5:20: error: compiz.h: No such file or directory
vector.h:34: error: 'CompScreen' has not been declared
vector.h:43: error: 'CompScreen' has not been declared
vector.h: In member function 'Vector Vector::toScreenSpace(int*) const':
vector.h:37: error: request for member 'width' in '* s', which is of non-class type 'int'
vector.h:38: error: request for member 'height' in '* s', which is of non-class type 'int'
vector.h: In member function 'Vector Vector::toCoordsSpace(int*) const':
vector.h:46: error: request for member 'width' in '* s', which is of non-class type 'int'
vector.h:47: error: request for member 'height' in '* s', which is of non-class type 'int'
matrix.h: At global scope:
matrix.h:15: error: expected ',' or '...' before '*' token
matrix.h:15: error: ISO C++ forbids declaration of 'CompTransform' with no type
matrix.h: In constructor 'Matrix::Matrix(int)':
matrix.h:15: error: 'mat' was not declared in this scope
matrix.h: In member function 'Matrix& Matrix::rotate(float, float, float, float)':
matrix.h:30: error: 'CompTransform' was not declared in this scope
matrix.h:30: error: expected primary-expression before ')' token
matrix.h:30: error: 'matrixRotate' was not declared in this scope
matrix.h: In member function 'Matrix& Matrix::scale(float, float, float)':
matrix.h:38: error: 'CompTransform' was not declared in this scope
matrix.h:38: error: expected primary-expression before ')' token
matrix.h:38: error: 'matrixScale' was not declared in this scope
matrix.h: In member function 'Matrix& Matrix::translate(float, float, float)':
matrix.h:46: error: 'CompTransform' was not declared in this scope
matrix.h:46: error: expected primary-expression before ')' token
matrix.h:46: error: 'matrixTranslate' was not declared in this scope
make: *** [build/matrix.lo] Error 1
amandine@amandine:~/compiz/screensaver$ 
```

---

### Post by lilalmond on 2008-04-08
Anyone please?

---

### Post by fnaax on 2008-04-18
have you tried this?

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

source: [http://kazbuntu.blogspot.com/2007/12/this-tutorial-assumes-that-1-you-have.html](http://kazbuntu.blogspot.com/2007/12/this-tutorial-assumes-that-1-you-have.html)

---

### Post by bmwman on 2008-04-21
I am also trying to install the Compiz screensaver plugin. I was able to download and extract it but have errors when trying to compile.

Here is the output:
emil@BAH806274EIC:~/compiz/screensaver$ make
compiling : vector.cpp -> build/vector.loIn file included from vector.cpp:1:
vector.h: In member function ‘Vector Vector::toScreenSpace(CompScreen*) const’:
vector.h:37: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:38: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h: In member function ‘Vector Vector::toCoordsSpace(CompScreen*) const’:
vector.h:46: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:47: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
make: *** [build/vector.lo] Error 1


Any help is apreciated!

---

### Post by jryprt on 2008-04-21
The guide came from [This](http://forum.compiz-fusion.org/showthread.php?t=5303) , post your errors there they will help, post your fix here for all to see .
It may be permissions problem look at [This](http://ubuntuforums.org/showthread.php?t=740034&page=2) thread post #15

---

