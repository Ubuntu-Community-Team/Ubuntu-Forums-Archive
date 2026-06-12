---
title: "Is this working for u?"
date: 2010-02-17
forum: Gaming &amp; Leisure
---

### Post by arnab_das on 2010-02-17
If you have some bandwidth to spare, could u check if the 64 bit version of this game xdriller is working for you? ( [http://xdriller.sourceforge.net/downloads.html](http://xdriller.sourceforge.net/downloads.html) )

its supposed to be a seriously awesome game, but i'm unable to launch the app. installation works perfectly but this is the error i get while launching it.

> Xdriller v0.7.2
Loading /home/username/.config/xdriller/config.cfg
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
FreeImage version: 3.10.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library /usr/lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_ParticleFX
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
Loading library /usr/lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.6.1 (Shoggoth)
OverlayElementFactory for type ColoredTextArea registered.
An exception has occured: OGRE EXCEPTION(7:InternalErrorException): /usr/share/xdriller/media.zip - error whilst opening archive: Unable to read zip file. in ZipArchive::checkZzipError at OgreZip.cpp (line 259)xdriller: src/HighScoreManager.cpp:22: static HighScoreManager& HighScoreManager::getSingleton(): Assertion `ms_Singleton' failed.
Aborted

any help? suggestions?

---

### Post by Bachstelze on 2010-02-17
Same error here.

---

### Post by arnab_das on 2010-02-17
> **Bachstelze said:**
> Same error here.

its a real shame though, coz the game is actually quite awesome.

[http://www.youtube.com/watch?v=y7NAk-az5-Y](http://www.youtube.com/watch?v=y7NAk-az5-Y)

---

### Post by Ferrat on 2010-02-18
have you checked that "/usr/share/xdriller/media.zip" is located where it should and accessible?

If so, then someone has broken unzip or you need some app installed that you are missing

---

### Post by arnab_das on 2010-02-18
> **Ferrat said:**
> have you checked that "/usr/share/xdriller/media.zip" is located where it should and accessible?

If so, then someone has broken unzip or you need some app installed that you are missing

that thing doesnt even exist! goodness, this is some bad programming.

---

### Post by portets on 2010-02-18
yeah, it looks good.

how do i run it though? i can't find the launcher. i've looked all over.
i even tried typing it into the terminal

---

### Post by arnab_das on 2010-02-18
> **portets said:**
> yeah, it looks good.

how do i run it though? i can't find the launcher. i've looked all over.
i even tried typing it into the terminal

you should download the appropriate file from the website (link in the very first post of this thread), and then install it.
next run it, will be in the game menu. however since it is not running from there, to check the error type "xdriller" from the terminal.

---

### Post by portets on 2010-02-18
i did all of that though, everything said it installed correctly. typing xdriller just says command not found.

should i restart my computer?

---

### Post by portets on 2010-02-18
okay, reinstalling it helped. buti got the same error you did.

it looks like the developer of the .deb package did something wrong.

the game is looking for the data in /usr/share/xdriller/
but it's actually in /usr/share/games/xdriller/

just open a terminal and type "sudo nautilus" then find the xdriller folder and copy and paste it into /usr/share/

now it works, and good game too!

---

### Post by durmieu on 2010-02-18
Hi,

Package updated, problem should be fixed now:

[https://launchpad.net/~durmieu/+archive/ppa/+files/xdriller_0.7.3-2_amd64.deb]("https://launchpad.net/%7Edurmieu/+archive/ppa/+files/xdriller_0.7.3-2_amd64.deb")

or visit [http://xdriller.sourceforge.net/downloads.html](http://xdriller.sourceforge.net/downloads.html)

if you get more crashes please send me a bug report to <durmieu @t users dot sourceforge dot net> with your $HOME/.config/xdriller/xdriller.log 

;)

---

### Post by arnab_das on 2010-02-18
> **portets said:**
> okay, reinstalling it helped. buti got the same error you did.

it looks like the developer of the .deb package did something wrong.

the game is looking for the data in /usr/share/xdriller/
but it's actually in /usr/share/games/xdriller/

just open a terminal and type "sudo nautilus" then find the xdriller folder and copy and paste it into /usr/share/

now it works, and good game too!

that worked like magic! thanks mate. :) but still the original should be debugged by the dev.

---

### Post by durmieu on 2010-02-18
Game data should be under /usr/share/games/xdriller in debian like distros. the problem should be fixed setting the correct paths un ~/.config/xdriller/config.cfg and ~/.config/xdriller/resources.cfg or updating to the patched version (aka 0.7.3-2), removing the user config files (rm ~/.config/xdriller/*) and launching xdriller again. The game should create new config files if the old ones are removed.

Please keep in mind that this game is still under development and there may be (and are) other bugs and things that need to be fixed. bug reports are always welkome.

durmieu at users(dot)sf(dot)net

---

### Post by arnab_das on 2010-02-18
> **durmieu said:**
> Game data should be under /usr/share/games/xdriller in debian like distros. the problem should be fixed setting the correct paths un ~/.config/xdriller/config.cfg and ~/.config/xdriller/resources.cfg or updating to the patched version (aka 0.7.3-2), removing the user config files (rm ~/.config/xdriller/*) and launching xdriller again. The game should create new config files if the old ones are removed.

Please keep in mind that this game is still under development and there may be (and are) other bugs and things that need to be fixed. bug reports are always welkome.

durmieu at users(dot)sf(dot)net

already sent u a bug report.

---

