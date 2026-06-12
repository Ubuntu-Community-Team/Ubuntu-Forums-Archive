---
title: "Ubuntu 11.10: Unreal Tournament GOTY can't install"
date: 2012-03-07
forum: Gaming &amp; Leisure
---

### Post by DemonSharkKisame on 2012-03-07
Mostly out of curiosity, and since I saw that my boxed copy of Unreal Tournament GOTY Edition supports Linux natively, I thought I'd give it the old college try since A: it looks fun, and B: I wanted to see if a 13-year-old game would still run in a modern Linux environment. Unfortunately, even with the help of [this Ubuntu Documentation]("https://help.ubuntu.com/community/Games/Native/UnrealTournament") page, I can't seem to get Unreal Tournament installed, much less working. I can get the .run file, but it seems I can't acquire the libraries required for the game. Is UT so old that Linux just doesn't run it anymore? :o

---

### Post by Toz on 2012-03-14
I was able to install and run UT/GOTY about a year ago without any problems. Unfortunately, I don't have it installed now. I remember that it was pretty straightforward to install, but I didn't follow the instructions that you linked to. Instead, have a look at the wineappdb page dedicated to it for installation isntructions: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=124]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=124").

---

### Post by DemonSharkKisame on 2012-03-27
> **Toz said:**
> I was able to install and run UT/GOTY about a year ago without any problems. Unfortunately, I don't have it installed now. I remember that it was pretty straightforward to install, but I didn't follow the instructions that you linked to. Instead, have a look at the wineappdb page dedicated to it for installation isntructions: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=124]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=124").

Thanks, though I'd prefer to run it natively rather than through Wine. At least Quake III Gold should work...

---

### Post by blueshead on 2012-03-29
> **DemonSharkKisame said:**
> Thanks, though I'd prefer to run it natively rather than through Wine. At least Quake III Gold should work...


You might also have a look at Quake Live (free).. It runs great in Ubuntu..

My tag is "swampy"

[http://www.quakelive.com]("http://www.quakelive.com")

---

### Post by nativenerd on 2012-07-21
> **DemonSharkKisame said:**
> Mostly out of curiosity, and since I saw that my boxed copy of Unreal Tournament GOTY Edition supports Linux natively, I thought I'd give it the old college try since A: it looks fun, and B: I wanted to see if a 13-year-old game would still run in a modern Linux environment. Unfortunately, even with the help of [this Ubuntu Documentation]("https://help.ubuntu.com/community/Games/Native/UnrealTournament") page, I can't seem to get Unreal Tournament installed, much less working. I can get the .run file, but it seems I can't acquire the libraries required for the game. Is UT so old that Linux just doesn't run it anymore? :o

I got the libraries installed by following:
[http://www.ubuntugeek.com/how-to-install-xmms-on-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-xmms-on-ubuntu-10-04-lucid.html)

Just follow along to install glib and libgtk, then don't bother with the last step to install the old XMMS...

---

### Post by R33D3M33R on 2012-07-21
Hello, thank you for sharing the solution. I will update the wiki with new links as soon as possible.

---

### Post by Limpalot on 2013-04-06
> **R33D3M33R said:**
> Hello, thank you for sharing the solution. I will update the wiki with new links as soon as possible.

I'm reviving this thread. :)
Is anybody still playing this on Ubunut?
I'm running Kubuntu Quantal and after a successful install and decompressing of maps I get 

```
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
Game class is 'UTIntro'
Level is Level Entry.MyLevel
Bringing Level Entry.MyLevel up for play (0)...
InitGame: 
Base Mutator is Entry.Mutator0
Browse: CityIntro.unr?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
LoadMap: CityIntro.unr?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Case-insensitive search: genfluid -> ..\Textures\GenFluid.utx
Collecting garbage
Purging garbage
-0.0ms Unloading: Package Render
Garbage: objects: 16417->16416; refs: 224678
Game class is 'UTIntro'
Level is Level CityIntro.MyLevel
Bringing Level CityIntro.MyLevel up for play (0)...
InitGame: ?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Base Mutator is CityIntro.Mutator1
Initialized moving brush tracker for Level CityIntro.MyLevel
Created and initialized a new SDL viewport.
Bound to UWeb.so
Team 255
Login: Player
Case-insensitive search: SoldierSkins -> ..\Textures\Soldierskins.utx
Possessed PlayerPawn: TMale2 CityIntro.TMale0
Input system initialized for SDLViewport0
Opening SDL viewport.
Bound to OpenGLDrv.so
Loaded render device class.
Initializing OpenGLDrv...
binding libGL.so.1
Resizing SDL viewport. X: 640 Y: 480
OpenGL
Signal: SIGSEGV [segmentation fault]
Aborting.
Exiting.
Name subsystem shut down
Allocation checking disabled
Segmentation fault (core dumped)
```

Does anyone have a clue?
I'd like to have UT running again...

Thanx

---

### Post by R33D3M33R on 2013-04-07
I just tried to run it again. It was and old install from the 2010. Since then I reinstalled the system several times and I'm currently on 12.10. Surprisingly, it ran OK.
Do you have drivers properly installed? Run ```
glxinfo | grep direct
``` just to be sure.

---

### Post by Limpalot on 2013-04-07
Returns

```
direct rendering: Yes

```

So I guess I do.
Thanks for the suggestion, though. :)

---

### Post by R33D3M33R on 2013-04-08
Ok, can you check if any of this is missing from glxinfo:

```
Init: Device supports: GL_EXT_bgra
Init: Device supports: GL_ARB_texture_compression
Init: Device supports: GL_EXT_texture_compression_s3tc
Init: Device supports: GL_EXT_texture_env_combine
Init: Device supports: GL_ARB_texture_env_combine
Init: Device supports: GL_EXT_texture_filter_anisotropic
Init: Device supports: GL_ATI_texture_env_combine3
Init: Device supports: GL_EXT_texture_lod_bias
Init: Device supports: GL_EXT_compiled_vertex_array
Init: Device supports: GL_EXT_secondary_color
Init: Device supports: GL_ARB_multitexture
Init: Device supports: GL_SGIS_generate_mipmap
Init: Device supports: GL_EXT_multi_draw_arrays
Init: Device supports: GL_ARB_vertex_program
```

BTW: what graphics card do you have?

---

### Post by SingingBush on 2013-04-08
I did an install a while back which still works fine for me. I wrote a guide here:
[http://www.samael.me.uk/2011/07/how-to-install-unreal-2004-on-ubuntu.html](http://www.samael.me.uk/2011/07/how-to-install-unreal-2004-on-ubuntu.html)

---

### Post by ank2 on 2014-02-09
You can use the software render device. Locate the UnrealTournament.ini and there you should findGameRenderDevice=OpenGLDrv.OpenGLRenderDevicecomment that so you have# GameRenderDevice=OpenGLDrv.OpenGLRenderDeviceand add the lineGameRenderDevice=SDLSoftDrv.SDLSoftwareRenderDeviceThat should work. Although graphics look bad now.

---

