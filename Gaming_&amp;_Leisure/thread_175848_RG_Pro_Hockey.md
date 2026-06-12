---
title: "RG Pro Hockey"
date: 2006-05-13
forum: Gaming &amp; Leisure
---

### Post by jon_z on 2006-05-13
Can anyone make an effective guide to make RG Pro hockey?  I cannot get this game to make for the life of me, trying all the versions..  

```
jon@Blackbox:~/Desktop/rph_stuff$ cd rgSDK
jon@Blackbox:~/Desktop/rph_stuff/rgSDK$ dir
debug     rgBMP    rgNetwork  rgPhysics  rgShadow    Version.txt
Makefile  rgBSP    rgOBJ      rgPort     rgStandard  windows
rg3DRom   rgCSG    rgOpenGL   rgProcess  rgTime
rgBezier  rgCurve  rgParse    rgRay      solaris
jon@Blackbox:~/Desktop/rph_stuff/rgSDK$ gedit Makefile
jon@Blackbox:~/Desktop/rph_stuff/rgSDK$ make all
cp -u rgBezier/rgBezier.h rgBMP/rgBMP.h rgBSP/rgBSP.h rgBSP/rgBSP_template.cpp rgCSG/rgCSG.h rgCurve/rgChaikin.h rgCurve/rgNURBS.h rgNetwork/rgNetwork.h rgOBJ/rgOBJ.h rgOpenGL/rgOpenGL.h rgParse/rgParse.h rgPhysics/rgPhysics.h rgPort/rgPort.h rgProcess/rgProcess.h rgRay/rgRay.h rgShadow/rgShadow.h rgStandard/rgError.h rgStandard/rgStandard.h rgTime/rgTime.h ../rgLibs
cp -u rg3DRom/rg3DRom.h rg3DRom/rg3DRom_file.h rg3DRom/rg3DRom_csg.h rg3DRom/rg3DRom_physics.h rg3DRom/rg3DRom_vertex_array.h ../rgLibs
g++ -Wall -Werror -I../rgLibs -DRGPORT_LITTLE_ENDIAN -DRG_UNSAFE_NORMALIZE -DRG_UNSAFE_MATRIX_MULT  -m3dnow -O3             -DLINUX_OS  -g -o debug/rgBezier.o \
                -c rgBezier/rgBezier.cpp
g++ -Wall -Werror -I../rgLibs -DRGPORT_LITTLE_ENDIAN -DRG_UNSAFE_NORMALIZE -DRG_UNSAFE_MATRIX_MULT  -m3dnow -O3             -DLINUX_OS  -g -o debug/rgBMP.o \
                -c rgBMP/rgBMP.cpp
g++ -Wall -Werror -I../rgLibs -DRGPORT_LITTLE_ENDIAN -DRG_UNSAFE_NORMALIZE -DRG_UNSAFE_MATRIX_MULT  -m3dnow -O3             -DLINUX_OS  -g -o debug/rgBSP.o \
                -c rgBSP/rgBSP.cpp
In file included from rgBSP/rgBSP.cpp:21:
../rgLibs/rgOpenGL.h:26:19: error: GL/gl.h: No such file or directory
../rgLibs/rgOpenGL.h:60: error: ‘GLuint’ does not name a type
../rgLibs/rgOpenGL.h: In constructor ‘rgGLTexture_ref_tag::rgGLTexture_ref_tag(int, int)’:
../rgLibs/rgOpenGL.h:73: error: ‘id’ was not declared in this scope
../rgLibs/rgOpenGL.h: At global scope:
../rgLibs/rgOpenGL.h:145: error: ‘GLuint’ does not name a type
../rgLibs/rgOpenGL.h:152: error: ‘GLuint’ does not name a type
../rgLibs/rgOpenGL.h:153: error: ‘GLuint’ does not name a type
../rgLibs/rgOpenGL.h:158: error: expected ‘,’ or ‘...’ before ‘id’
../rgLibs/rgOpenGL.h:158: error: ISO C++ forbids declaration of ‘GLuint’ with no type
../rgLibs/rgOpenGL.h:159: error: expected ‘,’ or ‘...’ before ‘id’
../rgLibs/rgOpenGL.h:159: error: ISO C++ forbids declaration of ‘GLuint’ with no type
../rgLibs/rgOpenGL.h:160: error: expected ‘,’ or ‘...’ before ‘id’
../rgLibs/rgOpenGL.h:160: error: ISO C++ forbids declaration of ‘GLuint’ with no type
../rgLibs/rgOpenGL.h:161: error: expected ‘,’ or ‘...’ before ‘id’
../rgLibs/rgOpenGL.h:161: error: ISO C++ forbids declaration of ‘GLuint’ with no type
../rgLibs/rgOpenGL.h: In member function ‘void rgGLTexture::bind() const’:
../rgLibs/rgOpenGL.h:100: error: ‘GL_TEXTURE_2D’ was not declared in this scope
../rgLibs/rgOpenGL.h:100: error: ‘textureID’ was not declared in this scope
../rgLibs/rgOpenGL.h:100: error: ‘glBindTexture’ was not declared in this scope
../rgLibs/rgOpenGL.h: In member function ‘void rgGLLight::set_pos() const’:
../rgLibs/rgOpenGL.h:182: error: ‘GL_POSITION’ was not declared in this scope
../rgLibs/rgOpenGL.h:182: error: ‘glLightfv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In member function ‘void rgGLLight::set_amb() const’:
../rgLibs/rgOpenGL.h:183: error: ‘GL_AMBIENT’ was not declared in this scope
../rgLibs/rgOpenGL.h:183: error: ‘glLightfv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In member function ‘void rgGLLight::set_dif() const’:
../rgLibs/rgOpenGL.h:184: error: ‘GL_DIFFUSE’ was not declared in this scope
../rgLibs/rgOpenGL.h:184: error: ‘glLightfv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In member function ‘void rgGLLight::set_spec() const’:
../rgLibs/rgOpenGL.h:185: error: ‘GL_SPECULAR’ was not declared in this scope
../rgLibs/rgOpenGL.h:185: error: ‘glLightfv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In member function ‘void rgGLLight::enable() const’:
../rgLibs/rgOpenGL.h:192: error: ‘glEnable’ was not declared in this scope
../rgLibs/rgOpenGL.h: In member function ‘void rgGLLight::disable() const’:
../rgLibs/rgOpenGL.h:193: error: ‘glDisable’ was not declared in this scope
../rgLibs/rgOpenGL.h: At global scope:
../rgLibs/rgOpenGL.h:292: error: expected ‘,’ or ‘...’ before ‘buf’
../rgLibs/rgOpenGL.h:293: error: ISO C++ forbids declaration of ‘GLint’ with no type
../rgLibs/rgOpenGL.h: In function ‘void glVertex(const rgVector&)’:
../rgLibs/rgOpenGL.h:304: error: ‘glVertex3fv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In function ‘void glNormal(const rgVector&)’:
../rgLibs/rgOpenGL.h:305: error: ‘glNormal3fv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In function ‘void glColor3(const rgVector&)’:
../rgLibs/rgOpenGL.h:306: error: ‘glColor3fv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In function ‘void glTexCoord(const rgVector&)’:
../rgLibs/rgOpenGL.h:307: error: ‘glTexCoord3fv’ was not declared in this scope
../rgLibs/rgOpenGL.h: In function ‘void glTexCoord2(const rgVector&)’:
../rgLibs/rgOpenGL.h:308: error: ‘glTexCoord2fv’ was not declared in this scope
rgBSP/rgBSP.cpp: In function ‘void rgBSP_NTTC_convex_hull_renderer(std::vector<rgBSPFace<rgBSP_NTTC_ExtData>, std::allocator<rgBSPFace<rgBSP_NTTC_ExtData> > >&, rgMatrix*, void*)’:
rgBSP/rgBSP.cpp:106: error: ‘GL_TEXTURE_2D’ was not declared in this scope
rgBSP/rgBSP.cpp:106: error: ‘glBindTexture’ was not declared in this scope
rgBSP/rgBSP.cpp:107: error: ‘GL_POLYGON’ was not declared in this scope
rgBSP/rgBSP.cpp:107: error: ‘glBegin’ was not declared in this scope
rgBSP/rgBSP.cpp:110: error: ‘glColor4f’ was not declared in this scope
rgBSP/rgBSP.cpp:111: error: ‘glTexCoord2f’ was not declared in this scope
rgBSP/rgBSP.cpp:115: error: ‘glEnd’ was not declared in this scope
rgBSP/rgBSP.cpp:127: error: ‘GL_TEXTURE_2D’ was not declared in this scope
rgBSP/rgBSP.cpp:127: error: ‘glBindTexture’ was not declared in this scope
rgBSP/rgBSP.cpp:128: error: ‘GL_POLYGON’ was not declared in this scope
rgBSP/rgBSP.cpp:128: error: ‘glBegin’ was not declared in this scope
rgBSP/rgBSP.cpp:131: error: ‘glColor4f’ was not declared in this scope
rgBSP/rgBSP.cpp:132: error: ‘glTexCoord2f’ was not declared in this scope
rgBSP/rgBSP.cpp:140: error: ‘glEnd’ was not declared in this scope
make: *** [debug/rgBSP.o] Error 1

```

---

### Post by Perfect Storm on 2006-05-14
Seems like you havn't installed the drivers for you graphic cards.

also needed:

```
sudo apt-get install freeglut3-dev
```

---

### Post by jon_z on 2006-05-14
```
The following packages have unmet dependencies.
  freeglut3-dev: Depends: xlibmesa-gl-dev but it is not installableor
                          libgl-dev
                 Depends: xlibmesa-glu-dev but it is not installableor
                          libglu-dev
E: Broken packages
jon@Blackbox:~$
```

```
!====================SYS===================!
testing/unstable
Linux version 2.6.15-22-k7 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sun May 7 17:27:47 UTC 2006

!===================CPU====================!
model name      : AMD Athlon(tm) 64 Processor 3200+
cpu MHz         : 2200.071
bogomips        : 4403.02
cache size      : 512 KB

!=================MEM======================!
MemTotal:      1034420 kB
MemFree:         18868 kB
SwapTotal:      835340 kB
SwapFree:       816452 kB

!================VIDEO=====================!
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5755 (8.24.8)


!============Gnome Version=================!
GDM 2.14.6

```

---

### Post by Perfect Storm on 2006-05-14
You may wait until the resolved the broken package dependency.
Do you have any unofficial stuff enable in your sourcelist that could break the dependency?

---

### Post by jon_z on 2006-05-14
wine, xgl, compiz

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 

#deb http://xgl.compiz.info/ dapper main
#deb http://www.beerorkid.com/compiz/ dapper main


## Wine
#deb http://wine.sourceforge.net/apt/ binary/



```

---

### Post by Perfect Storm on 2006-05-14
If you have compiz and xgl in your sourcelist, that could explain. I usually had them in my sourcelist until I found out it breaks stuff if you want to compile.

---

### Post by jon_z on 2006-05-14
i have them commented out, i sudo apt-get update 'd and tried again, no avail. see my source list above,,

---

### Post by Perfect Storm on 2006-05-14
If you can find the list of package that you installed by xgl and compiz (just look at the howto to found out) then go to [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/) and get them there.


Edit: also if you want to gaming on Ubuntu and/or linux you might disable xgl and compiz.

---

### Post by jon_z on 2006-05-14
following this guide: [https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati)

i installed:
1. libglitz1
2. libglitz-glx1
3. xserver-xgl
4. libgl1-mesa
5. libsvg
6. libsvg-cairo
7. compiz
8. compiz-gnome
9. gset-compiz

not sure how to use that webpage to get the packages..

*edit* i have it set up so that xgl/compiz is a different session.

---

### Post by Perfect Storm on 2006-05-14
Okay now find the package at the link I gave you.

To install them:

```
sudo dpkg -i XXXXXXXXXX.deb
```

---

### Post by jon_z on 2006-05-14
which packages am i looking for? the xgl/compiz ones? or the dependency for freelgut?

---

### Post by Perfect Storm on 2006-05-14
freeglut

---

### Post by jon_z on 2006-05-14
making sure im doing the right thing, am i configuring this package from source or no?

*edit*  man i was stupid.. click on i386 gives me the deb :-D

---

### Post by Perfect Storm on 2006-05-14
freeglut? You should get the .deb package.

---

### Post by jon_z on 2006-05-14
```
jon@Blackbox:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package freeglut3-dev.
(Reading database ... 89890 files and directories currently installed.)
Unpacking freeglut3-dev (from freeglut3-dev_2.4.0-4_i386.deb) ...
dpkg: dependency problems prevent configuration of freeglut3-dev:
 freeglut3-dev depends on xlibmesa-gl-dev | libgl-dev; however:
  Package xlibmesa-gl-dev is not installed.
  Package libgl-dev is not installed.
 freeglut3-dev depends on xlibmesa-glu-dev | libglu-dev; however:
  Package xlibmesa-glu-dev is not installed.
  Package libglu-dev is not installed.
dpkg: error processing freeglut3-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 freeglut3-dev
jon@Blackbox:~/Desktop$

```

xlibmesa-gl-dev is not available on the package page..  and its an endless line of dependency's

---

### Post by Perfect Storm on 2006-05-14
Hmmm...I'm not sure what else to do, since the the xgl/compiz stuff have replaced alot of packages.

---

### Post by jon_z on 2006-05-14
should i try installing a sarge package to fulfill a dependency?

---

### Post by Perfect Storm on 2006-05-14
It's not advisable. You could end with a broken system. But it's up to you to take the chance.

---

### Post by jon_z on 2006-05-14
alright, sounds like im just going to have to scratch this project then.. I've tried searching, are there any other hockey games for *nix?

---

### Post by Perfect Storm on 2006-05-14
Well you could do a clean install of dapper and just forget xgl/compiz if you want 3D game.


There's a hockey manager game: [http://doc.gwos.org/index.php/Ice_Hockey_Manager](http://doc.gwos.org/index.php/Ice_Hockey_Manager)

Mhockey - [http://www.linuxgames.com/mhockey/](http://www.linuxgames.com/mhockey/)

---

### Post by jon_z on 2006-05-14
haha, i even have a problem with that, java being funky for dapper messes with it, i get it to run but it crashes into it.

---

### Post by jon_z on 2006-05-14
I'll be home from University in a few days, I think I will just purchase NHL'06 for PS2

---

### Post by Perfect Storm on 2006-05-14
If you get java from the repo then uninstall it and use this instead: [http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

Before you follow the guide you need:
```
sudo apt-get install build-essential
```

---

### Post by jon_z on 2006-05-14
great guide, worked nice...testing with hockey manager. ill edit the results.


*edit*  perfect thank you very much A.I.

---

