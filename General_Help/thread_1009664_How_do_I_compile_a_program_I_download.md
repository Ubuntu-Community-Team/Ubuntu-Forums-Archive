---
title: "How do I compile a program I download?"
date: 2008-12-12
forum: General Help
---

### Post by ToddAndMargo on 2008-12-12
I all.  I am new to Ubunto.  "make" do not seem to work.  gcc is installed.
How do I compile a program I download?

root@VB-KUbuntu:/home/todd/Desktop/k9copy/k9copy-2.1.0-Source# make
make: *** No targets specified and no makefile found.  Stop.

# make install
make: *** No rule to make target `install'.  Stop.

What am I missing?

Many thanks,
-T

---

### Post by Jermcb on 2008-12-12
Assuming you have already extracted the package to a given folder and you are currently in the same folder in the Terminal window you would have to first configure the package before you can install it...

Try typing in:
"./configure"

if you get no errors then type in
"make"

Then

"make install"

---

### Post by ToddAndMargo on 2008-12-12
# pwd
/home/todd/Desktop/k9copy/k9copy-2.1.0-Source

# ./configure
bash: ./configure: No such file or directory

# ls -aF
./                       CTestTestfile.cmake            k9copy_open.desktop
../                      data/                          k9copy.pot
cmake/                   .directory                     k9copy.shell*
CMakeCache.txt           Doxyfile                       k9copyui.rc
CMakeFiles/              hi16-app-k9copy.png*           k9play*
cmake_install.cmake      hi32-app-k9copy.png*           k9play.shell*
CMakeLists.txt           hi48-app-k9copy.png*           k9xineplayer.shell*
cmake_uninstall.cmake    icons/                         lib/
config.h                 install_manifest.txt           main.cpp
config.h.cmake           k9copy_assistant.desktop       po/
COPYING                  k9copy_assistant_open.desktop  README
CPackConfig.cmake        k9copy.desktop                 src/
CPackSourceConfig.cmake  k9copy.kdevses


What am I doing wrong?

---

### Post by Jermcb on 2008-12-12
Have you tried reading the "install_manifest.txt" file you have in that folder? They generally give install instruction in the readme.txt files or some variant thereof...

Otherwise, do you have "cmake" installed on your computer?

---

### Post by ToddAndMargo on 2008-12-12
The manifest file only contains a list of files.

$ which cmake
/usr/bin/cmake

Cmake exists, but give me all kinds of errors.

Any idea what I am doing wrong?

-T


# cmake .
-- The CXX compiler identification is unknown
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path orname.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

  It fails with the following output:





  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:1 (project)


CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path orname.
CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring done

---

### Post by mc4man on 2008-12-12
The k9 your trying to build is for kde4.x, are you using that? If not, you should be building  a 1.xx version of k9 instead.

From the read me in your source

> !!!!!ATTENTION!!!!!

Before starting the build you may need to setup the KDE4 environment variables.
To do this open Project->Project Options and then look at the "Run" and the "Make" 
pages. Each of these two has an environment variables widget in which you have
to fill in the right values for the variables already listed.

After setting up the variables you'll also need to run cmake inside the build
directory. This can not be done by kdevelop as a KDE4 environment is needed
when running cmake to find KDE4. Open the integrated konsole and change to the build
subdirectory. Then setup a KDE4 environment and run "cmake ../".


While it will be incomplete you should run 
```
sudo apt-get build-dep k9copy
```


Or just run this and use the repo version
```

sudo apt-get install k9copy
```

---

### Post by ToddAndMargo on 2008-12-12
> **mc4man said:**
> The k9 your trying to build is for kde4.x, are you using that?

KDE 4.1

Any idea what the variables are I am to set?

> While it will be incomplete you should run 
```
sudo apt-get build-dep k9copy
```

Or just run this and use the repo version
```

sudo apt-get install k9copy
```

The apt version of k9copy is from an older version.  The version I downloaded
is 2.1.0.  The older version won't read newer DVD's. I was hoping the newer
version had it figured out.

-T

---

### Post by mc4man on 2008-12-13
I don't have a kde 4 install so never tried building there, wouldn't know.

Maybe this;

[http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy)

---

### Post by ToddAndMargo on 2008-12-13
> **mc4man said:**
> 
[http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy)


Oh mama!  Much easier than compiling!  Thank!

-T

---

