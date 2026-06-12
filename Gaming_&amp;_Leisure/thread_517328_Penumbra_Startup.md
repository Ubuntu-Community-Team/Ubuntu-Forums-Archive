---
title: "Penumbra Startup"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by n_hendrick on 2007-08-04
Okay I have penumbra from the digital download but when I try to run it as user it freezes the screen and spits me back into X with a changed resolution and no mouse. But when I run as root the game loads and is playable. It used to run as user I don't know what I've done to my system since I purchased it a few months back...its probably just some strange permissions error or something but heres my hpl.log file
```

-------- THE HPL ENGINE LOG ------------

Creating Engine Modules
--------------------------------------------------------
 Creating graphics module
 Creating system module
 Creating resource module
 Creating input module
 Creating sound module
 Creating physics module
 Creating ai module
 Creating scene module
--------------------------------------------------------

Initializing Resources Module
--------------------------------------------------------
 Creating resource managers
 Misc Creation
--------------------------------------------------------

Initializing Graphics Module
--------------------------------------------------------
 Init low level graphics
 Setting video mode: 800 x 600 - 32 bpp
 Init Glee...OK
 Setting up OpenGL
  Max texture image units: 16
  Max texture coord units: 8
  Two sided stencil: 1
  Vertex Buffer Object: 1
  Anisotropic filtering: 1
  Max Anisotropic degree: 16
  Multisampling: 1
  Vertex Program: 1
  Fragment Program: 1
  NV Register Combiners: 1
  NV Register Combiners Stages: 8
  ATI Fragment Shader: 0
 Creating graphic systems
  Creating Renderer2D
  Renderer2D created
  Creating Renderer3D
   Load Renderer3D gpu programs:
    Extrude
    Diffuse
    Fog
   Creating fog textures: Solid Additive Alpha 
   init sky box
  Renderer3D created
 Creating screen buffers size 800.000000 : 600.000000
 Creating programs
  RendererPostEffects created
 Adding engine materials
--------------------------------------------------------

Initializing Sound Module
--------------------------------------------------------
 Initializing OpenAL.
  Trying to open audio device... Deleting ATI shader to 0

```

I'm not getting any errors but when I load the game it spits out something about not being able to start mcop and the I should try the command ulimit -c unlimited, still won't work as user. Oh yeah, I'm running Feisty with 100 series nvidia card and a audigy 2 zs soundboard, and I have a Geforce 7600. Thanks in advance...

---

### Post by Kubunteando on 2007-08-05
Try to close all other applications before starting Penumbra.
It seems it stop when trying to get access to the Sound Device.

If that does not help, disable aRTS (Ubuntu sound system) before starting the game. Penumbra may want exclusive access to the sound device and this is hold by Ubuntu sound system aRTS.

---

### Post by n_hendrick on 2007-08-06
thanks I'll give it a go tonight, be back later....

---

### Post by cisforcojo on 2007-08-07
Their support forums are REALLY good I must add. 

[http://frictionalgames.com/forum/forumdisplay.php?fid=24](http://frictionalgames.com/forum/forumdisplay.php?fid=24)

---

