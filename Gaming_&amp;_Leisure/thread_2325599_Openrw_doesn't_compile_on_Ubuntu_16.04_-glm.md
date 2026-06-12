---
title: "Openrw doesn't compile on Ubuntu 16.04 -glm"
date: 2016-05-23
forum: Gaming &amp; Leisure
---

### Post by mateo14 on 2016-05-23
Hi

I tried to install different versions of Libglm, and I tried different tricks, but none of them worked:


cmake ../ -DCMAKE_BUILD_TYPE=Release
-- Found SFML 2.3.2 in /usr/include
CMake Error at CMakeLists.txt:61 (find_package):
  Could not find a package configuration file provided by "glm" with any of
  the following names:

    glmConfig.cmake
    glm-config.cmake

  Add the installation prefix of "glm" to CMAKE_PREFIX_PATH or set "glm_DIR"
  to a directory containing one of the above files.  If "glm" provides a
  separate development package or SDK, be sure it has been installed.


-- Configuring incomplete, errors occurred!
See also "/home/gbudny/Downloads/openrw-master/build/CMakeFiles/CMakeOutput.log".

Can you help me?

---

### Post by ZoiaGuyver on 2016-05-23
Well the file you should need is libglm-dev It's basically a "header" part for OpenGL mathematics. Did you install the libglm from repos or did you try to build them?

The error is basically telling you it can't find any glm, I know the one in 16.04 is 0.9.7.2 so it may be that this OpenRW needs something newer?

---

### Post by mateo14 on 2016-05-23
I tried to install from repo GLM 0.9.7.2, 0.9.7.4 etc. on Ubuntu 16.04, and I also noticed the same issue on Ubuntu 14.04 with the much older version of glm. 


I do not know how to compile GLM from the source code, but I copied those headers to /usr/include/glm, and it did not work.

I used cmake-gui to compile glm:

sudo apt-get install cmake-qt-gui

---

