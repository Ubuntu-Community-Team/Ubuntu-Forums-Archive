---
title: "rogs of rods game problem"
date: 2008-05-07
forum: Gaming &amp; Leisure
---

### Post by Periswell on 2008-05-07
hi

i have just installed the game rigs of rods but when i press the button to make it start, nothing happens. when i ran it in terminal, this is what the shell script says...

> joshua@utnubu:~$ '/usr/share/games/rigsofrods/RoR'
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DevIL version: Developer's Image Library (DevIL) 1.6.7 Oct 27 2007
DevIL image formats: bmp dib cut dcx dds gif hdr ico cur jpg jpe jpeg lif mdl mng jng pcx pic pix png pbm pgm pnm ppm psd pdd psp pxr sgi bw rgb rgba tga vda icb vst tif tiff wal xpm raw 
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library ./RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library ./Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library ./Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library ./Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.4.5 (Eihort)
RoR log: RoR.log
Ogre config: ogre.cfg
OverlayElementFactory for type SpinControl registered.
Creating resource group Bootstrap
Added resource location 'data/OgreCore' of type 'FileSystem' to resource group 'Bootstrap'
Creating resource group ET
Added resource location 'data/ET' of type 'FileSystem' to resource group 'ET'
Added resource location '.' of type 'FileSystem' to resource group 'General'
Added resource location 'data' of type 'FileSystem' to resource group 'General'
Added resource location 'data/map' of type 'FileSystem' to resource group 'General'
Added resource location 'data/terrains' of type 'FileSystem' to resource group 'General'
Added resource location 'data/trucks' of type 'FileSystem' to resource group 'General'
Added resource location 'data/objects' of type 'FileSystem' to resource group 'General'
Added resource location 'data/paged' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/configs' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/fonts' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/imagesets' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/layouts' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/looknfeel' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/lua_scripts' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/schemes' of type 'FileSystem' to resource group 'General'
Creating resource group Packs
Added resource location 'packs' of type 'FileSystem' to resource group 'Packs'
Added resource location '/home/joshua/.rigsofrods/packs/' of type 'FileSystem' to resource group 'Packs'
registering skidmark factory
MovableObjectFactory for type 'Skidmark' registered.
registering colored text overlay factory
OverlayElementFactory for type ColoredTextArea registered.


Configuration error: Run the RoRconfig program first.

*-*-* OGRE Shutdown
*-*-* OGRE Shutdown
Unregistering ResourceManager for type Compositor
Unregistering ResourceManager for type Font
Unregistering ResourceManager for type Skeleton
Unregistering ResourceManager for type Mesh
Unregistering ResourceManager for type HighLevelGpuProgram
Uninstalling plugin: Cg Program Manager
Plugin successfully uninstalled
Unloading library ./Plugin_CgProgramManager
Uninstalling plugin: Octree & Terrain Scene Manager
Plugin successfully uninstalled
Unloading library ./Plugin_OctreeSceneManager
Uninstalling plugin: ParticleFX
Plugin successfully uninstalled
Unloading library ./Plugin_ParticleFX
Uninstalling plugin: GL RenderSystem
******************************
*** Stopping GLX Subsystem ***
******************************
Plugin successfully uninstalled
Unloading library ./RenderSystem_GL
Unregistering ResourceManager for type Material


and this is what the program says...

> root@utnubu:/home/joshua# '/usr/share/games/rigsofrods/RoR.bin'
/usr/share/games/rigsofrods/RoR.bin: error while loading shared libraries: libOIS-1.1.0.so: cannot open shared object file: No such file or directory


im not sure what to do, it told me to install some packages for it and the config files but once installed, it says the same thing. here is what the config shell script file says in terminal...

> 
root@utnubu:/home/joshua# '/usr/share/games/rigsofrods/RoRConfig'
/usr/share/games/rigsofrods/RoRConfig.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory


and this is what the program says....

> root@utnubu:/home/joshua# '/usr/share/games/rigsofrods/RoRConfig.bin'
/usr/share/games/rigsofrods/RoRConfig.bin: error while loading shared libraries: libOgreMain-1.4.5.so: cannot open shared object file: No such file or directory


all help will be most appreciated. thanks in advance.

-josh

---

### Post by Perfect Storm on 2008-05-07
Are you on Ubuntu 8.04?

---

### Post by Periswell on 2008-05-07
yep

-josh

---

### Post by Periswell on 2008-05-07
bump

---

### Post by Perfect Storm on 2008-05-08
Use the Ubuntu .deb instead of the script: [http://wiki.rigsofrods.com/index.php?title=Installation_Guide#Ubuntu.2FDebian](http://wiki.rigsofrods.com/index.php?title=Installation_Guide#Ubuntu.2FDebian)

---

### Post by Periswell on 2008-05-08
i had use the .deb package and installed it via synaptic. 

-josh

---

### Post by Perfect Storm on 2008-05-08
ok. This might work, but the libOIS is "old" on hardy.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install libois1 libtiff4 libogre14
sudo ln -s /usr/lib/libOIS.so.1.0.0 /usr/lib/libOIS.so.1.1.0.so
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libOgreMain.so.14.0.5 /usr/lib/libOgreMain-1.4.5.so
```

---

### Post by Periswell on 2008-05-08
thanks a bunch mate, it works now!

thanks

---

### Post by Perfect Storm on 2008-05-08
My pleasure ^_^

---

