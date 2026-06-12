---
title: "Rigs of Rods not running"
date: 2010-04-07
forum: Gaming &amp; Leisure
---

### Post by fallenshadow on 2010-04-07
I would appreciate if somebody could help me to get Rigs of Rods working on my machine.

I need somebody kinda technical to help me out here...

Here is my error log:
```

14:15:32: Creating resource group General
14:15:32: Creating resource group Internal
14:15:32: Creating resource group Autodetect
14:15:32: SceneManagerFactory for type 'DefaultSceneManager' registered.
14:15:32: Registering ResourceManager for type Material
14:15:32: Registering ResourceManager for type Mesh
14:15:32: Registering ResourceManager for type Skeleton
14:15:32: MovableObjectFactory for type 'ParticleSystem' registered.
14:15:32: OverlayElementFactory for type Panel registered.
14:15:32: OverlayElementFactory for type BorderPanel registered.
14:15:32: OverlayElementFactory for type TextArea registered.
14:15:32: Registering ResourceManager for type Font
14:15:32: ArchiveFactory for archive type FileSystem registered.
14:15:32: ArchiveFactory for archive type Zip registered.
14:15:32: DevIL version: Developer's Image Library (DevIL) 1.6.7 May 11 2008
14:15:32: DevIL image formats: bmp dib cut dcx dds gif hdr ico cur jpg jpe jpeg lif mdl mng jng pcx pic pix png pbm pgm pnm ppm psd pdd psp pxr sgi bw rgb rgba tga vda icb vst tif tiff wal xpm raw 
14:15:32: DDS codec registering
14:15:32: Registering ResourceManager for type HighLevelGpuProgram
14:15:32: Registering ResourceManager for type Compositor
14:15:32: MovableObjectFactory for type 'Entity' registered.
14:15:32: MovableObjectFactory for type 'Light' registered.
14:15:32: MovableObjectFactory for type 'BillboardSet' registered.
14:15:32: MovableObjectFactory for type 'ManualObject' registered.
14:15:32: MovableObjectFactory for type 'BillboardChain' registered.
14:15:32: MovableObjectFactory for type 'RibbonTrail' registered.
14:15:32: Loading library ./RenderSystem_GL
14:15:32: Installing plugin: GL RenderSystem
14:15:32: OpenGL Rendering Subsystem created.
14:15:32: Plugin successfully installed
14:15:32: Loading library ./Plugin_ParticleFX
14:15:32: Installing plugin: ParticleFX
14:15:32: Particle Emitter Type 'Point' registered
14:15:32: Particle Emitter Type 'Box' registered
14:15:32: Particle Emitter Type 'Ellipsoid' registered
14:15:32: Particle Emitter Type 'Cylinder' registered
14:15:32: Particle Emitter Type 'Ring' registered
14:15:32: Particle Emitter Type 'HollowEllipsoid' registered
14:15:32: Particle Affector Type 'LinearForce' registered
14:15:32: Particle Affector Type 'ColourFader' registered
14:15:32: Particle Affector Type 'ColourFader2' registered
14:15:32: Particle Affector Type 'ColourImage' registered
14:15:32: Particle Affector Type 'ColourInterpolator' registered
14:15:32: Particle Affector Type 'Scaler' registered
14:15:32: Particle Affector Type 'Rotator' registered
14:15:32: Particle Affector Type 'DirectionRandomiser' registered
14:15:32: Particle Affector Type 'DeflectorPlane' registered
14:15:32: Plugin successfully installed
14:15:32: Loading library ./Plugin_OctreeSceneManager
14:15:32: Installing plugin: Octree & Terrain Scene Manager
14:15:32: Plugin successfully installed
14:15:32: Loading library ./Plugin_CgProgramManager
14:15:32: Installing plugin: Cg Program Manager
14:15:32: Plugin successfully installed
14:15:32: *-*-* OGRE Initialising
14:15:32: *-*-* Version 1.4.5 (Eihort)
14:15:32: RoR log: RoR.log
14:15:32: Ogre config: ogre.cfg
14:15:32: OverlayElementFactory for type SpinControl registered.
14:15:32: Creating resource group Bootstrap
14:15:32: Added resource location 'data/OgreCore' of type 'FileSystem' to resource group 'Bootstrap'
14:15:32: Creating resource group ET
14:15:32: Added resource location 'data/ET' of type 'FileSystem' to resource group 'ET'
14:15:32: Added resource location '.' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data/map' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data/terrains' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data/trucks' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data/objects' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data/paged' of type 'FileSystem' to resource group 'General'
14:15:32: Added resource location 'data/cache' of type 'FileSystem' to resource group 'General'
14:15:32: Creating resource group InternalPacks
14:15:32: Added resource location 'data/packs' of type 'FileSystem' to resource group 'InternalPacks'
14:15:32: Creating resource group Packs
14:15:32: Added resource location 'packs' of type 'FileSystem' to resource group 'Packs'
14:15:32: Added resource location '/home/dylan/.rigsofrods/packs/' of type 'FileSystem' to resource group 'Packs'
14:15:32: registering skidmark factory
14:15:32: MovableObjectFactory for type 'Skidmark' registered.
14:15:32: registering colored text overlay factory
14:15:32: OverlayElementFactory for type ColoredTextArea registered.
14:15:32: *-*-* OGRE Shutdown
14:15:32: *-*-* OGRE Shutdown
14:15:32: Unregistering ResourceManager for type Compositor
14:15:32: Unregistering ResourceManager for type Font
14:15:32: Unregistering ResourceManager for type Skeleton
14:15:32: Unregistering ResourceManager for type Mesh
14:15:32: Unregistering ResourceManager for type HighLevelGpuProgram
14:15:32: Uninstalling plugin: Cg Program Manager
14:15:32: Plugin successfully uninstalled
14:15:32: Unloading library ./Plugin_CgProgramManager
14:15:32: Uninstalling plugin: Octree & Terrain Scene Manager
14:15:32: Plugin successfully uninstalled
14:15:32: Unloading library ./Plugin_OctreeSceneManager
14:15:32: Uninstalling plugin: ParticleFX
14:15:32: Plugin successfully uninstalled
14:15:32: Unloading library ./Plugin_ParticleFX
14:15:32: Uninstalling plugin: GL RenderSystem
14:15:32: ******************************
*** Stopping GLX Subsystem ***
******************************
14:15:32: Plugin successfully uninstalled
14:15:32: Unloading library ./RenderSystem_GL
14:15:32: Unregistering ResourceManager for type Material

```

Its a problem with OGRE I think, especially where it says "OGRE shutdown". 

Anyone have ideas how to fix this problem? :confused:

---

### Post by fallenshadow on 2010-04-07
Its ok guys I solved this myself. :)

Having fun now! If only I had a better PC to run this. :P

---

