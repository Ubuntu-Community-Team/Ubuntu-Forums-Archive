---
title: "Trying to Install Wyrmsun..."
date: 2017-03-20
forum: Gaming &amp; Leisure
---

### Post by joepro83 on 2017-03-20
I've been having issues with Wyrmsun crashing in Steam. So I figured I'd try to install it outside of Steam. I've installed all necessary programs in order to get the Stratagus Engine to work (hopefully I did the majority of it correctly anyway). But I'm getting an error and I'm not sure how to correct it. Still learning Linux and have been trying (on my own) to do some things. But I'm kind of at a wall. Here's what I got when try to do:
```
cmake .. && make
```
```
-- The C compiler identification is GNU 5.4.0
-- The CXX compiler identification is GNU 5.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Checking for module 'maemo-version'
--   No package 'maemo-version' found
-- Found Lua51: /usr/lib/x86_64-linux-gnu/liblua5.1.so;/usr/lib/x86_64-linux-gnu/libm.so (found version "5.1.5") 
-- Found ZLIB: /usr/local/lib/libz.so (found version "1.2.11") 
-- Found PNG: /usr/local/lib/libpng.so (found version "1.6.28") 
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
CMake Error at /usr/local/share/cmake-3.8/Modules/FindPackageHandleStandardArgs.cmake:137 (message):
  Could NOT find SDL (missing: SDL_LIBRARY SDL_INCLUDE_DIR)
Call Stack (most recent call first):
  /usr/local/share/cmake-3.8/Modules/FindPackageHandleStandardArgs.cmake:377 (_FPHSA_FAILURE_MESSAGE)
  /usr/local/share/cmake-3.8/Modules/FindSDL.cmake:190 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:641 (find_package)


-- Configuring incomplete, errors occurred!
See also "/home/joe/Downloads/stratagus_2.3.0.orig/build/CMakeFiles/CMakeOutput.log".
See also "/home/joe/Downloads/stratagus_2.3.0.orig/build/CMakeFiles/CMakeError.log".
```

I'm guessing I didn't install SDL correctly. As for the Call Stack stuff, I'm at a total loss of understanding. I don't even know what Call Stack means for that matter. Any guidance is welcome.

---

### Post by uNoubu8a on 2017-03-20
> **joepro83 said:**
> ```
-- Configuring incomplete, errors occurred!
See also "/home/joe/Downloads/stratagus_2.3.0.orig/build/CMakeFiles/CMakeOutput.log".
See also "/home/joe/Downloads/stratagus_2.3.0.orig/build/CMakeFiles/CMakeError.log".
```

I'm guessing I didn't install SDL correctly. As for the Call Stack stuff, I'm at a total loss of understanding. I don't even know what Call Stack means for that matter. Any guidance is welcome.

Hi,

Compiling software from source, brave man :KS

Perhaps posting the output of the two logs mentioned above would assist the guru's here to assist. (Personally I have compiled perhaps five applications from source in a history of Linux that started in 1999, so for me figuring out why yours is crashing in Steam is a more feasible course of action).  Also add what version of Ubuntu you are running and your hardware/drivers etc.

Edit: Just installed the game through Steam and fired up a scenario, so far so good... makes me think of Warcraft 1/2 :)

Edit2: There is a neat little application that can quickly get all of your system information that is used a lot on other forums (but I seldom see it being used here) called inxi.  To install it and get it to generate some information on your system you can use:

```
sudo apt-get install inxi
inxi -b
```

---

