---
title: "Doom3 falls back on Mesa software rasterizer ?"
date: 2011-11-14
forum: Gaming &amp; Leisure
---

### Post by HolgerB on 2011-11-14
Hi there,

I just wanted to play Doom 3 again. So I grabbed the sh-installer, copied over the pak files and started doom3. So far, so good.

Unfortunately Doom3 somehow fails to detect that I am running hardware accelerated OpenGL. At least that is what I think from the Doom3 init log:
```

----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Software Rasterizer
...

```Well I can at least confirm that the Gallium radeon driver works fine since I get this output from glxinfo | grep OpenGL
```

OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20

```OS is Xubuntu 11.10 x64
Hardware:
AMD E350 
8 GB RAM
ATI HD4670 (additional graphic adapter)

3D acceleration in Darkplaces works perfectly as I can play Kleshik without hickups.
Is Doom3 using an older lib which still is software OpenGL only ? :confused:

One thing that also puzzles me: Some of my screensavers seem also be running on software mode after I switched from fglrx back to radeon.

Edit: I should have mentioned that I fully removed fglrx with all components following the guide in the ubuntu troubleshooting guide.

Any ideas ?

TIA,
Holger

---

### Post by GenPFault on 2011-12-08
> Xubuntu 11.10 **x64**

**EDIT:** Ok, on a clean 11.10 install these packages did the trick for me:

```

gcc-multilib g++-multilib
libx11-6:i386 libxext6:i386
libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
libasound2:i386 libasound2-plugins:i386

```

Use LIBGL_DEBUG=verbose to [double-check that doom3 isn't trying to use the old libstdc++.so.6 it ships with.]("http://phoronix.com/forums/showthread.php?65039-Will-Mesa-Gallium3D-Work-With-The-Open-Source-Doom-3&p=240110#post240110")  If it is, just move that and libgcc_s.so.1 off into a subdirectory so it won't see them.

When I did the above I went from <1FPS to an easy 60 on my Radeon 6950.  

Time to tackle Quake 4...awesome, the same "get rid of the crappy old libraries" procedure works there too.  Well, after installing [a 32-bit libtxc_dxtn]("http://people.freedesktop.org/~cbrill/libtxc_dxtn/") that is:

```

sudo apt-get install build-essential gcc-multilib g++-multilib libgl1-mesa-dev
CFLAGS="-m32" LDFLAGS="-m32" ./configure --prefix=/usr --libdir=/usr/lib32
make
sudo make install

```

You may or may not need to export R600_ENABLE_S3TC=1 to get S3TC compression working.

---

