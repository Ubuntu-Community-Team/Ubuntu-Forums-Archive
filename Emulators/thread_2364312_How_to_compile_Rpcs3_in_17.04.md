---
title: "How to compile Rpcs3 in 17.04"
date: 2017-06-21
forum: Emulators
---

### Post by sensenku on 2017-06-21
Hi, I fond PS3 emulator in Ubuntu, but i could not compile it, please help me.
Here's video. I did compiling and get this message in terminal

```
mehman@hp:~/rpcs3/build$ cmake ..
-- The C compiler identification is GNU 6.3.0
-- The CXX compiler identification is GNU 6.3.0
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
-- No build type selected, default to Release
-- Found ZLIB: /usr/lib/x86_64-linux-gnu/libz.so (found version "1.2.11") 
CMake Warning (dev) at 3rdparty/libpng/CMakeLists.txt:317 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.


  The LOCATION property should not be read from target "png16_static".  Use
  the target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.


This warning is for project developers.  Use -Wno-dev to suppress it.


CMake Warning at rpcs3/CMakeLists.txt:8 (find_package):
  By not providing "FindQt5.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "Qt5", but
  CMake did not find one.


  Could not find a package configuration file provided by "Qt5" (requested
  version 5.8) with any of the following names:


    Qt5Config.cmake
    qt5-config.cmake


  Add the installation prefix of "Qt5" to CMAKE_PREFIX_PATH or set "Qt5_DIR"
  to a directory containing one of the above files.  If "Qt5" provides a
  separate development package or SDK, be sure it has been installed.




Minimum supported Qt5 version is 5.8! You have version  installed, please upgrade!
CMake Error at rpcs3/CMakeLists.txt:23 (message):
  Most distros do not provide an up-to-date version of Qt.


  If you're on Ubuntu or Linux Mint, there are PPAs you can use to install an
  up-to-date qt5 version.


          [https://launchpad.net/~beineri/+archive/ubuntu/opt-qt59-xenial](https://launchpad.net/~beineri/+archive/ubuntu/opt-qt59-xenial)
          [https://launchpad.net/~beineri/+archive/ubuntu/opt-qt59-trusty](https://launchpad.net/~beineri/+archive/ubuntu/opt-qt59-trusty)


  just make sure to run


      source /opt/qt59/bin/qt59-env.sh


  before re-running cmake




-- Configuring incomplete, errors occurred!
See also "/home/mehman/rpcs3/build/CMakeFiles/CMakeOutput.log".
mehman@hp:~/rpcs3/build$ 





[https://www.youtube.com/watch?v=BYKZEFUdtFI](https://www.youtube.com/watch?v=BYKZEFUdtFI)
```

---

### Post by deadflowr on 2017-06-22
*Thread moved to **Emulators**.*

---

### Post by adec2 on 2017-06-22
[COLOR=#24292E][FONT=SFMono-Regular]sudo apt-get install cmake build-essential libasound2-dev libopenal-dev libglew-dev zlib1g-dev libedit-dev libvulkan-dev libudev-dev git qt5-default

[/FONT][/COLOR]
[LIST=1]
[*]git clone [https://github.com/RPCS3/rpcs3.git](https://github.com/RPCS3/rpcs3.git)
[*]cd rpcs3/
[*]git submodule update --init
[*]cmake CMakeLists.txt && make GitVersion && make
[/LIST]

---

