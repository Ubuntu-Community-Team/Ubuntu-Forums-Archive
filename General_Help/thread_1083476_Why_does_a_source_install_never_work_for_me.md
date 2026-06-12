---
title: "Why does a source install never work for me?"
date: 2009-03-01
forum: General Help
---

### Post by Firestem4 on 2009-03-01
Every time i try to install something from source, I follow the directions word for word but it NEVER works. What gives? I'll give you a recent example, maybe you can help.

I had tried to install a theme QtCurve from kde-look.org [http://kde-look.org/content/show.php/QtCurve+(KDE4%2C+KDE3%2C+%26+Gtk2+Theme)?content=40492](http://kde-look.org/content/show.php/QtCurve+(KDE4%2C+KDE3%2C+%26+Gtk2+Theme)?content=40492)

I downloaded the 8.10 source. I updated to the latest cmake

i did exactly what it says:

```
mkdir build
cd build
cmake ..
make
make install
```

I get this

```
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4$ cd build
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at /usr/share/cmake-2.6/Modules/FindQt4.cmake:1421 (MESSAGE):
  Qt qmake not found!
Call Stack (most recent call first):
  CMakeLists.txt:72 (find_package)
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4$ make
make: *** No rule to make target `make'.  Stop.
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4$ make install
make: *** No rule to make target `install'.  Stop.

```
Note: 
The how-to install lists no rule if one is needed... I'm not sure whats going on...ANYTHING ive ever tried to make just ends up not being able to.. What am I doing wrong?

---

### Post by taurus on 2009-03-01
> **Firestem4 said:**
> Every time i try to install something from source, I follow the directions word for word but it NEVER works. What gives? I'll give you a recent example, maybe you can help.

I had tried to install a theme QtCurve from kde-look.org [http://kde-look.org/content/show.php/QtCurve+(KDE4%2C+KDE3%2C+%26+Gtk2+Theme)?content=40492](http://kde-look.org/content/show.php/QtCurve+(KDE4%2C+KDE3%2C+%26+Gtk2+Theme)?content=40492)

I downloaded the 8.10 source. I updated to the latest cmake

i did exactly what it says:

```
mkdir build
cd build
cmake ..
make
make install
```

I get this

```
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4$ cd build
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at /usr/share/cmake-2.6/Modules/FindQt4.cmake:1421 (MESSAGE):
  **[COLOR="Red"]Qt qmake not found![/COLOR]**
Call Stack (most recent call first):
  CMakeLists.txt:72 (find_package)
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4$ make
make: *** No rule to make target `make'.  Stop.
icarus@icarus-linux:~/Desktop/QtCurve-KDE4-0.61.4$ make install
make: *** No rule to make target `install'.  Stop.

```
Note: 
The how-to install lists no rule if one is needed... I'm not sure whats going on...ANYTHING ive ever tried to make just ends up not being able to.. What am I doing wrong?

Looks like you need the qt4-dev-tools.

---

### Post by Firestem4 on 2009-03-01
I couldn't figure out what qmake was. apt-cache show didnt result anything. I didn't know that was the dev tool. Thanks.

(Before i posted this i found someone made a .deb of this so I had used that.) But I am still uncertain why other things never worked. =/

---

### Post by taurus on 2009-03-01
If you want to build something from source, you need to hunt down all the dependencies and developing packages that it needs.

What other things never work?

---

### Post by Firestem4 on 2009-03-01
Ive tried to compile a few programs, a widget too I believe. I haven't tried to do anything in a while so I can not really remember anymore what I had tried to compile.

If you need to get all of the dependencies, How can you if the source does not list them?

---

### Post by Xiong Chiamiov on 2009-03-01
That's what the configure script (or in this case, cmake) does; you have to look at what it says is missing, then figure out which packages you need to install to provide those.  The developers can't tell you which package you'll need, as the package names differ from distro-to-distro.

---

### Post by Firestem4 on 2009-03-03
Ok, thanks for explaining. 

Can anyone explain the arguements (...i forget if they're called something else lol). for instance like cmake -(something)

what does cmake .. do? Its not in the help.

and what arguements should I use/know about make/cmake; if any?

---

### Post by heindsight on 2009-03-03
> **Firestem4 said:**
> Ok, thanks for explaining. 

Can anyone explain the arguements (...i forget if they're called something else lol). for instance like cmake -(something)

what does cmake .. do? Its not in the help.

and what arguements should I use/know about make/cmake; if any?

Try reading the manuals:
cmake: [http://manpages.ubuntu.com/manpages/intrepid/en/man1/cmake.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/cmake.1.html)
make: [http://manpages.ubuntu.com/manpages/intrepid/en/man1/make.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/make.1.html)

Or just use the commands:
```
man cmake
```
and
```
man make
```

---

