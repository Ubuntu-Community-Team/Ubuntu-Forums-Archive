---
title: "Broken OGRE"
date: 2007-11-07
forum: Gaming &amp; Leisure
---

### Post by Vadi on 2007-11-07
For some reason I can't get any of my ogre-based games to work anymore. I tried Funglouds and Tile racer, both quit with similar ending messages:

```
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::createRenderWindow "Those Funny Funguloids!", 1024x768 fullscreen  miscParams: FSAA=0 title=Those Funny Funguloids! 
GLXWindow::create
Parsing miscParams
GLXWindow::create -- Entering full screen mode
GLXWindow::create -- Best visual is 85
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  27
  Current serial number in output stream:  32
vadi@vadi-laptop:~/TileRacer$ 
```

```
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::createRenderWindow "Tile Racer", 1024x768 fullscreen  miscParams: FSAA=0 title=Tile Racer 
GLXWindow::create
Parsing miscParams
GLXWindow::create -- Entering full screen mode
GLXWindow::create -- Best visual is 85
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  27
  Current serial number in output stream:  32
*-*-* OGRE Shutdown
*-*-* OGRE Shutdown
Unregistering ResourceManager for type Compositor
Unregistering ResourceManager for type Font
Unregistering ResourceManager for type Skeleton
Unregistering ResourceManager for type Mesh
Unregistering ResourceManager for type HighLevelGpuProgram
Uninstalling plugin: 
Plugin successfully uninstalled
Unloading library ../lib_linux/Plugin_CgProgramManager.so
Uninstalling plugin: Octree & Terrain Scene Manager
Plugin successfully uninstalled
Unloading library ../lib_linux/Plugin_OctreeSceneManager.so
terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create
Aborted (core dumped)
vadi@vadi-laptop:~/TileRacer$ 
```

Anyone have any ideas on how to fix this?

---

### Post by kutsyy on 2008-04-20
I had this problem recently. I think you have to install or turn on nvidia(ati) driver.

---

### Post by Vadi on 2008-04-20
I don't use the laptop that had this problem anymore, and I don't remember if I solved the issue. Sorry :/

---

