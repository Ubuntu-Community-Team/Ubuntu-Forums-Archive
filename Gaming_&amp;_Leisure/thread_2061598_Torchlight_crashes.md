---
title: "Torchlight crashes"
date: 2012-09-22
forum: Gaming &amp; Leisure
---

### Post by JaySeeJC on 2012-09-22
The humble indie bundle 6 version of torchlight, installed from the software center, keeps crashing. I really don't know where to start, as this is a proprietary game and so gives very little to work with in terms of debugging. The entire output from start to crash is here:
```

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
FreeImage version: 3.13.1
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,bay,bmq,cr2,crw,cs1,dc2,dcr,dng,erf,fff,hdr,k25,kdc,mdc,mos,mrw,nef,orf,pef,pxn,raf,raw,rdc,sr2,srf,arw,3fr,cine,ia,kc2,mef,nrw,qtk,rw2,sti,drf,dsc,ptx,cap,iiq,rwz
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library lib/OGRE/Plugin_ParticleFX
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
Loading library lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.6.5 (Shoggoth)
Error: signal: 11

/opt/torchlight/Torchlight.bin.x86(_ZN10LinuxUtils13crash_handlerEi+0x1f)[0x9377fa7]
[0xf77c9400]
/opt/torchlight/lib/libOgreMain-1.6.5.so(+0x1a36c1)[0xf753c6c1]
/opt/torchlight/lib/libOgreMain-1.6.5.so(+0x1a4d69)[0xf753dd69]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre5ImageD1Ev+0x48)[0xf74e3f98]
lib/OGRE/RenderSystem_GL.so(+0x2ca5f)[0xf5a8ca5f]
lib/OGRE/RenderSystem_GL.so(+0x2970f)[0xf5a8970f]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Resource4loadEb+0x1c1)[0xf75cd351]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZNK4Ogre16TextureUnitState12ensureLoadedEj+0x5e)[0xf76a9f1e]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre16TextureUnitState5_loadEv+0x3f)[0xf76aa1df]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre4Pass5_loadEv+0x35)[0xf75943e5]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre9Technique5_loadEv+0x3d)[0xf769cfbd]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Material8loadImplEv+0x35)[0xf7507eb5]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Resource4loadEb+0x1c1)[0xf75cd351]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Resource5touchEv+0x1a)[0xf75ccbaa]
/opt/torchlight/lib/libOgreMain-1.6.5.so(+0x171d28)[0xf750ad28]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre11RenderQueue13addRenderableEPNS_10RenderableEht+0x61)[0xf75b0851]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre11RenderQueue13addRenderableEPNS_10RenderableEh+0x34)[0xf75b0c84]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre14StaticGeometry14MaterialBucket14addRenderablesEPNS_11RenderQueueEhf+0x88)[0xf7681868]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre14StaticGeometry9LODBucket14addRenderablesEPNS_11RenderQueueEhf+0x55)[0xf76818f5]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre14StaticGeometry6Region18_updateRenderQueueEPNS_11RenderQueueE+0x46)[0xf7681956]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre11RenderQueue20processVisibleObjectEPNS_13MovableObjectEPNS_6CameraEbPNS_24VisibleObjectsBoundsInfoE+0x87)[0xf75b10e7]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre10OctreeNode17_addToRenderQueueEPNS_6CameraEPNS_11RenderQueueEbPNS_24VisibleObjectsBoundsInfoE+0x70)[0xf5a3fe70]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0xcf)[0xf5a39e4f]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x313)[0xf5a3a093]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager19_findVisibleObjectsEPNS_6CameraEPNS_24VisibleObjectsBoundsInfoEb+0x103)[0xf5a3a303]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12SceneManager12_renderSceneEPNS_6CameraEPNS_8ViewportEb+0x328)[0xf75f2ad8]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre6Camera12_renderSceneEPNS_8ViewportEb+0x2e)[0xf748ad3e]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Viewport6updateEv+0x30)[0xf76b6fe0]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12RenderTarget10updateImplEv+0x5d)[0xf75c9bbd]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12RenderTarget6updateEb+0x2c)[0xf75c951c]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12RenderSystem23_updateAllRenderTargetsEb+0x71)[0xf75b6fb1]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre4Root23_updateAllRenderTargetsEv+0x33)[0xf75e63e3]

```If anyone has any idea how to fix ogre it would be great, as i think it's impeding a couple other indie games too.

---

### Post by Sonsum on 2012-09-23
> **JaySeeJC said:**
> The humble indie bundle 6 version of torchlight, installed from the software center, keeps crashing. I really don't know where to start, as this is a proprietary game and so gives very little to work with in terms of debugging. The entire output from start to crash is here:
```

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
FreeImage version: 3.13.1
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,bay,bmq,cr2,crw,cs1,dc2,dcr,dng,erf,fff,hdr,k25,kdc,mdc,mos,mrw,nef,orf,pef,pxn,raf,raw,rdc,sr2,srf,arw,3fr,cine,ia,kc2,mef,nrw,qtk,rw2,sti,drf,dsc,ptx,cap,iiq,rwz
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library lib/OGRE/Plugin_ParticleFX
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
Loading library lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.6.5 (Shoggoth)
Error: signal: 11

/opt/torchlight/Torchlight.bin.x86(_ZN10LinuxUtils13crash_handlerEi+0x1f)[0x9377fa7]
[0xf77c9400]
/opt/torchlight/lib/libOgreMain-1.6.5.so(+0x1a36c1)[0xf753c6c1]
/opt/torchlight/lib/libOgreMain-1.6.5.so(+0x1a4d69)[0xf753dd69]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre5ImageD1Ev+0x48)[0xf74e3f98]
lib/OGRE/RenderSystem_GL.so(+0x2ca5f)[0xf5a8ca5f]
lib/OGRE/RenderSystem_GL.so(+0x2970f)[0xf5a8970f]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Resource4loadEb+0x1c1)[0xf75cd351]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZNK4Ogre16TextureUnitState12ensureLoadedEj+0x5e)[0xf76a9f1e]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre16TextureUnitState5_loadEv+0x3f)[0xf76aa1df]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre4Pass5_loadEv+0x35)[0xf75943e5]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre9Technique5_loadEv+0x3d)[0xf769cfbd]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Material8loadImplEv+0x35)[0xf7507eb5]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Resource4loadEb+0x1c1)[0xf75cd351]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Resource5touchEv+0x1a)[0xf75ccbaa]
/opt/torchlight/lib/libOgreMain-1.6.5.so(+0x171d28)[0xf750ad28]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre11RenderQueue13addRenderableEPNS_10RenderableEht+0x61)[0xf75b0851]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre11RenderQueue13addRenderableEPNS_10RenderableEh+0x34)[0xf75b0c84]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre14StaticGeometry14MaterialBucket14addRenderablesEPNS_11RenderQueueEhf+0x88)[0xf7681868]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre14StaticGeometry9LODBucket14addRenderablesEPNS_11RenderQueueEhf+0x55)[0xf76818f5]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre14StaticGeometry6Region18_updateRenderQueueEPNS_11RenderQueueE+0x46)[0xf7681956]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre11RenderQueue20processVisibleObjectEPNS_13MovableObjectEPNS_6CameraEbPNS_24VisibleObjectsBoundsInfoE+0x87)[0xf75b10e7]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre10OctreeNode17_addToRenderQueueEPNS_6CameraEPNS_11RenderQueueEbPNS_24VisibleObjectsBoundsInfoE+0x70)[0xf5a3fe70]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0xcf)[0xf5a39e4f]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x176)[0xf5a39ef6]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager10walkOctreeEPNS_12OctreeCameraEPNS_11RenderQueueEPNS_6OctreeEPNS_24VisibleObjectsBoundsInfoEbb+0x313)[0xf5a3a093]
lib/OGRE/Plugin_OctreeSceneManager.so(_ZN4Ogre18OctreeSceneManager19_findVisibleObjectsEPNS_6CameraEPNS_24VisibleObjectsBoundsInfoEb+0x103)[0xf5a3a303]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12SceneManager12_renderSceneEPNS_6CameraEPNS_8ViewportEb+0x328)[0xf75f2ad8]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre6Camera12_renderSceneEPNS_8ViewportEb+0x2e)[0xf748ad3e]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre8Viewport6updateEv+0x30)[0xf76b6fe0]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12RenderTarget10updateImplEv+0x5d)[0xf75c9bbd]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12RenderTarget6updateEb+0x2c)[0xf75c951c]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre12RenderSystem23_updateAllRenderTargetsEb+0x71)[0xf75b6fb1]
/opt/torchlight/lib/libOgreMain-1.6.5.so(_ZN4Ogre4Root23_updateAllRenderTargetsEv+0x33)[0xf75e63e3]

```If anyone has any idea how to fix ogre it would be great, as i think it's impeding a couple other indie games too.

Doesn't HB have a contact us form? The developers would understand this much more than the people here, because this may be a linux or library problem and not an Ubuntu-specific one.

---

### Post by JaySeeJC on 2012-09-23
> **Sonsum said:**
> Doesn't HB have a contact us form? The developers would understand this much more than the people here, because this may be a linux or library problem and not an Ubuntu-specific one.
Thanks for the advise. I've shot them off an email and am now just waiting for a reply. I'll post here if i resolve the issue and how i did it.

---

