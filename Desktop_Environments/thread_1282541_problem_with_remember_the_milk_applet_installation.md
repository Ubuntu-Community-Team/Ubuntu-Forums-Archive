---
title: "problem with remember the milk applet installation"
date: 2009-10-04
forum: Desktop Environments
---

### Post by moskito on 2009-10-04
Hi!

First, sorry for my english. 

The problem is with the installation of the plasma widget "remember the milk". 

About a month ago the Remember the milk applet stop working. 
[http://ubuntuforums.org/showthread.php?p=796005](http://ubuntuforums.org/showthread.php?p=796005)

But now, there is a new version:
[https://bugs.kde.org/show_bug.cgi?id=199224](https://bugs.kde.org/show_bug.cgi?id=199224)

I tried to compile and i cant install de new version. When i tried to compile i did these things:

```
svn co svn://anonsvn.kde.org/home/kde/trunk/KDE/kdeplasma-addons/applets/rememberthemilk
```

Now i can compile:

```
cmake .
```

But after this, the terminal gave this error:

```
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
CMake Error at CMakeLists.txt:17 (kde4_add_ui_files):                     
  Unknown CMake command "kde4_add_ui_files".                              


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more    
  information run "cmake --help-policy CMP0000".                             
This warning is for project developers.  Use -Wno-dev to suppress it.        

-- Configuring incomplete, errors occurred!
```

After i tried to change cmakelists.txt adding "*find_package(KDE4 REQUIRED)*" or "*find_package(KDE4)*".

But finally dont work. I dont know what to do.

Thanks in advance

---

