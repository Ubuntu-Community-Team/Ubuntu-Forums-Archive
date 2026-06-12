---
title: "plasmoid installation"
date: 2008-03-02
forum: Desktop Environments
---

### Post by honorguard on 2008-03-02
Hi, 
I looked at 
[http://www.kde-look.org/content/show.php/Email+Notify?content=75194]("http://www.kde-look.org/content/show.php/Email+Notify?content=75194")
and I think, it's usefull plasmoid.
I found following howto install plasmoid:
[http://www.kde-look.org/help/index.php?type=70&PHPSESSID=c7d3091939a0e62a75d52e53875fc161]("http://www.kde-look.org/help/index.php?type=70&PHPSESSID=c7d3091939a0e62a75d52e53875fc161")
I tried it. But I have a problem after following command:
```
cmake -DCMAKE_INSTALL_PREFIX=/usr/lib/kde4/
```
I requested following error:
```
root@jakub-laptop:/home/jakub/download/emailnotify# cmake -DCMAKE_INSTALL_PREFIX=/usr/lib/kde4/
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error: The C compiler "/usr/bin/gcc" is not able to compile a simple test program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build
make[1]: Entering directory `/home/jakub/download/emailnotify/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/jakub/download/emailnotify/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/usr/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/jakub/download/emailnotify/CMakeFiles/CMakeTmp/testCCompiler.c
/home/jakub/download/emailnotify/CMakeFiles/CMakeTmp/testCCompiler.c:4:19: error: stdio.h: No such file or directory
/home/jakub/download/emailnotify/CMakeFiles/CMakeTmp/testCCompiler.c: In function &#8216;main&#8217;:
/home/jakub/download/emailnotify/CMakeFiles/CMakeTmp/testCCompiler.c:12: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make[1]: Leaving directory `/home/jakub/download/emailnotify/CMakeFiles/CMakeTmp'
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done
```
And after it "make" doesn't work.
Have somebody some solvation?
PS: My english isn't good.
THNX!!!

---

### Post by wkdude18 on 2008-05-24
I had the same problem. I was trying to install the Pretty Tasks Manager, but none of the installation instructions work.

This is frustrating!!:(

---

### Post by The_Doctor on 2008-07-15
Looks like you don't have a compiler. Run sudo apt-get install gcc g++ and try again.

---

