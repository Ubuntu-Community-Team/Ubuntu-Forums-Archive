---
title: "X64 steam openGL direct render woes"
date: 2013-04-03
forum: Gaming &amp; Leisure
---

### Post by linux4life01 on 2013-04-03
Hello fellow gamers. I am having issues with steam. it pops up with a warning every time I launch the program  ```
OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457
```

however when I run ```
 glxinfo |grep "direct render"
```
I get ```
direct rendering:yes
```

my graphics card is a Radeon HD 7660G (A10-APU) integrated
I installed the 13.11 beta drivers with no problem (other than that ugly watermark;))
I installed ia32-libs

thank you for your time and help in this endeavor.

---

### Post by linux4life01 on 2013-04-04
On the steam forums I was told I have to have Mesa-libs:i386 installed. However when I install that it removes Mesa x64.

---

### Post by ak0ska on 2013-05-09
I have a similar problem, with an HD6850. Did you find a solution? or anyone else? :)

---

### Post by cartman_ on 2013-06-08
I am running Linux Mint 13, 64b

For me adding the user to the video group did not help, nor installing the mesa-libs:i386 - yes it started steam without the error, but I was unable to start Left 4 Dead 2 Beta, said that I dont have S3TC texture support.
So messing around more I ended up with a fresh OS installation with updates, installed the AMD Catalyst 13.4, installed Steam, added myself to the 'video' group and then without installing the mesa-libs:i386 specifically (i think steam installed something like that) 
I was able to run Steam and Left 4 Dead 2 Beta, with this script:

```
#!/usr/bin/env bash
export LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu:/usr/lib/i386-linux-gnu/dri:/usr/lib/i386-linux-gnu/fglrx:/usr/lib/i386-linux-gnu:gconv

steam
```

basically it points Steam to use the 32bit libraries.

```
dpkg -l | grep :i386
ii  gcc-4.6-base:i386                      4.6.3-1ubuntu5                          GCC, the GNU Compiler Collection (base package)
ii  libc6:i386                             2.15-0ubuntu10.4                        Embedded GNU C Library: Shared libraries
ii  libdrm-intel1:i386                     2.4.43-0ubuntu0.0.1                     Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a:i386                  2.4.43-0ubuntu0.0.1                     Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                    2.4.43-0ubuntu0.0.1                     Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2:i386                           2.4.43-0ubuntu0.0.1                     Userspace interface to kernel DRM services -- runtime
ii  libexpat1:i386                         2.0.1-7.2ubuntu1.1                      XML parsing C library - runtime library
ii  libffi6:i386                           3.0.11~rc1-5                            Foreign Function Interface library runtime
ii  libgcc1:i386                           1:4.6.3-1ubuntu5                        GCC support library
ii  libgl1-mesa-dri:i386                   8.0.4-0ubuntu0.5                        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:i386                   8.0.4-0ubuntu0.5                        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:i386                     8.0.4-0ubuntu0.5                        free implementation of the GL API -- shared library
ii  libllvm3.0:i386                        3.0-4ubuntu1                            Low-Level Virtual Machine (LLVM), runtime library
ii  libpciaccess0:i386                     0.12.902-1ubuntu0.2                     Generic PCI access library for X
ii  libstdc++6:i386                        4.6.3-1ubuntu5                          GNU Standard C++ Library v3
ii  libx11-6:i386                          2:1.4.99.1-0ubuntu2.1                   X11 client-side library
ii  libx11-xcb1:i386                       2:1.4.99.1-0ubuntu2.1                   Xlib/XCB interface library
ii  libxau6:i386                           1:1.0.6-4                               X11 authorisation library
ii  libxcb-glx0:i386                       1.8.1-1ubuntu0.2                        X C Binding, glx extension
ii  libxcb1:i386                           1.8.1-1ubuntu0.2                        X C Binding
ii  libxdamage1:i386                       1:1.1.3-2build1                         X11 damaged region extension library
ii  libxdmcp6:i386                         1:1.1.0-4                               X11 Display Manager Control Protocol library
ii  libxext6:i386                          2:1.3.0-3ubuntu0.1                      X11 miscellaneous extension library
ii  libxfixes3:i386                        1:5.0-4ubuntu4.1                        X11 miscellaneous 'fixes' extension library
ii  libxxf86vm1:i386                       1:1.1.1-2ubuntu0.1                      X11 XFree86 video mode extension library
ii  zlib1g:i386                            1:1.2.3.4.dfsg-3ubuntu4                 compression library - runtime
```

```
glxinfo | grep OpenGL
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104
OpenGL shading language version string: 4.20
```

My card is an Asus Radeon HD 7950 Direct CU II TOP V2 (actually have two of them)
The OS reinstallation is surely not a necessary step :) but mine got messed up. For some reason I didnt have libGL and related stuff anymore, and neither reinstalling the packages nor drivers did not help at the time, so I reinstalled.

---

