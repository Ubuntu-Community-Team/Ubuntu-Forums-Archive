---
title: "Penumbra crashing"
date: 2009-01-27
forum: Gaming &amp; Leisure
---

### Post by DrSeptapus on 2009-01-27
i had penumbra installed a while ago. i decided to go back and play it, upon running it i got a black screen for a couple seconds and then it crashed. I ran it in the terminal and got:

root@Mainframe:/home/brock/Games/Penumbra# ./penumbra
open /dev/[sound/]dsp: Device or resource busy
Segmentation fault
Penumbra exited unexpectedly, please check
/root/.frictionalgames/Penumbra Overture/Episode1/hpl.log
for any error messages
Also try running
ulimit -c unlimited
And re-running Penumbra and try and recreate the error
then submit the generated core file or stack trace

hpl.log says:

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
  Max texture image units: 32
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
  Trying to open audio device... 

I am lost. can somebody help me out here?

---

