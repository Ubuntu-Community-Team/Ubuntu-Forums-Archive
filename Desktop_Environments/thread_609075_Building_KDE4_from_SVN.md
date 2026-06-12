---
title: "Building KDE4 from SVN"
date: 2007-11-10
forum: Desktop Environments
---

### Post by thekidder on 2007-11-10
I'm attempting to build KDE4 from SVN using the instructions from techbase. However, I'm running into a couple of problems.

When I try to build kdelibs, I get an error saying that Soprano 1.97 or greater is needed. I then grab kdesupport and try to build that. Now I get an error saying:
```
$ cmakekde
CMake Error: Qt qmake not found!
-- Configuring done

```

Running qmake in a terminal runs fine however.

Any ideas?

---

### Post by Nano Geek on 2007-11-10
Did you try running this?```
 sudo apt-get build-dep kdelibs4
```

---

### Post by thekidder on 2007-11-10
It gives me the error "Unable to find source package for kdelibs4". I tried kdelibs5 (pretty sure the kubuntu KDE4 kdelibs package is kdelibs5), and it worked, but I still have the same problem.

---

### Post by Nano Geek on 2007-11-10
Hmm. Did you try this?```
sudo apt-get build-dep kde4base
```

---

### Post by kugn on 2007-11-11
The original problem, ie the lack of soprano, should be solved by 
apt-get install libsoprano-dev
The version you want is only available in the Hardy repositories though. Gutsy's version remains at 1.95

As for the qmake error, the instructions page you referred to from Techbase says this:
If qmake wasn't found and you are using Debian packages, /usr/bin/qmake probably points to a wrong qmake version. To fix this run as root:
update-alternatives --config qmake
This presumes that the Qt4 path is correctly set.


As an alternative to building KDE4 on those instructions, there is a script that largely automates the building process. Check out [http://kdesvn-build.kde.org/](http://kdesvn-build.kde.org/) and [http://techbase.kde.org/Getting_Started/Build/kdesvn-build](http://techbase.kde.org/Getting_Started/Build/kdesvn-build)

---

### Post by thekidder on 2007-11-16
Everything built using the kdesvn-build script. I had to remove libsoprano first so that kdelibs would use the version in kdesupport.

Thanks :)

---

### Post by Rul on 2007-11-23
Did you have to do something to build KDE4 in a different session? or you just used kdesvn-build? I don't want to mess my current kde 3

---

### Post by marsmissionaries on 2007-11-25
Enabling backports, and then installing all of the dependencies, and then disabling backports allows kdesvn-build script to run flawlessly.

---

### Post by gamma on 2007-11-26
I've built KDE4 via SVN successfully, but I don't have the system configuration applications. There isn't a Kcontrol or Systemconfig application. Am I missing a module or are these applications not included by default yet? I was assuming it'd be in kdebase..

---

### Post by GeneralZod on 2007-11-26
> **gamma said:**
> I've built KDE4 via SVN successfully, but I don't have the system configuration applications. There isn't a Kcontrol or Systemconfig application. Am I missing a module or are these applications not included by default yet? I was assuming it'd be in kdebase..

The executable name should be

```

systemsettings

```

---

### Post by gamma on 2007-11-26
> **GeneralZod said:**
> The executable name should be

```

systemsettings

```
Aha. Thanks! It always helps to know the application name :).

---

### Post by DLGandalf on 2007-12-17
i've got the problem with soprano too
I removed the 1.95 version, and checked out the kdesupport/soprano

But when I try to compile kdelibs it gives me the following error:

```

-- Configuring done
gandalf@gandalfpc:~/kde/build/KDE/kdelibs$ cs
gandalf@gandalfpc:~/kde/src/KDE/kdelibs$ cmakekde
-- Found Qt-Version 4.3.2 (using /usr/bin/qmake-qt4)
-- Found X11: /usr/lib/libX11.so
-- Building kdelibs...
-- Found KDE4 kconfig_compiler preprocessor: /home/gandalf/kde/build/KDE/kdelibs/bin/./kconfig_compiler.shell
-- Found KDE4 automoc: /home/gandalf/kde/build/KDE/kdelibs/bin/./kde4automoc.shell
-- Found Strigi: /usr/lib/libstreams.so
CMake Error: Error in cmake code at
/home/gandalf/kde/src/KDE/kdelibs/cmake/modules/FindSoprano.cmake:78:
FILE Internal CMake error when trying to open file: /usr/include/soprano/version.h for reading.
Current CMake stack:
[2]     /home/gandalf/kde/src/KDE/kdelibs/cmake/modules/FindSoprano.cmake
[1]     /home/gandalf/kde/src/KDE/kdelibs/CMakeLists.txt
CMake Error: Error in cmake code at
/home/gandalf/kde/src/KDE/kdelibs/cmake/modules/FindSoprano.cmake:79:
STRING sub-command REGEX, mode MATCH needs at least 5 arguments total to command.
Current CMake stack:
[2]     /home/gandalf/kde/src/KDE/kdelibs/cmake/modules/FindSoprano.cmake
[1]     /home/gandalf/kde/src/KDE/kdelibs/CMakeLists.txt
-- Found Soprano: /usr/lib/libsoprano.so
-- Found Soprano includes: /usr/include
-- Found Soprano Index: /usr/lib/libsopranoindex.so
-- Found Soprano Client: /usr/lib/libsopranoclient.so


```

someone have an idea


ps
is the following correct:
I have got 
kde/
-----kdesupport/
---------------------soprano
-----KDE/
-----------kdelibs
-----------kdebase
-----------kdepimlibs

or should the kdesupport be in an other location

---

### Post by GeneralZod on 2007-12-17
> **DLGandalf said:**
> <snip>

Try deleting your CMakeCache.txt from your kdelibs build directory.

---

### Post by DLGandalf on 2007-12-17
thanks
How could I have known this without your help?

---

### Post by TSAMoloTOFf on 2007-12-23
Hi!
There is a problem when I try to compile KDE4RC from svn by kdesvn:

It says that in /kdebase/workspace/kdm/kfrontend/themer/kdmitem,cpp
on line 600 is a syntax error  in that line:

```
QDebug ds=kDebug(); 
```

What should I do?

PS Ubuntu Gutsy AMD64 kernel 2.6.22-14

---

### Post by GeneralZod on 2007-12-23
> **TSAMoloTOFf said:**
> Hi!
There is a problem when I try to compile KDE4RC from svn by kdesvn:

It says that in /kdebase/workspace/kdm/kfrontend/themer/kdmitem,cpp
on line 600 is a syntax error  in that line:

```
QDebug ds=kDebug(); 
```

What should I do?

PS Ubuntu Gutsy AMD64 kernel 2.6.22-14

This is a known issue with compiling in Release Mode.  It's being worked on.

---

