---
title: "Very poor performance in armyops250"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by peragrate on 2008-08-12
I've read through all the threads on armyops and I can't find my exact situation or a solution... so please forgive me for flogging a dead horse!

I'm on Hardy. AAO installed without a hitch (.run.) It starts without a hitch. It loads games (training) without a hitch. But the performance is terrible.

I've tried shutting everything down, like compiz, before running the game (using System Monitor.) Closing all my widgets (only two.) I've edited the config file ( /usr/local/games/armyops/System/Default.ini) to change the driver selection:

[Engine.Engine]
;RenderDevice=D3DDrv.D3DRenderDevice
RenderDevice=D3D9Drv.D3D9RenderDevice **(My selection: stops game freeze.)**
;RenderDevice=Engine.NullRenderDevice
;RenderDevice=OpenGLDrv.OpenGLRenderDevice **(Default)**
;RenderDevice=PixoDrv.PixoRenderDevice

and increased the cache memory from 64 to 256mb:

[Engine.GameEngine]
CacheSizeMegs=256 **(used to be 64mb)**

I've even: export SDL_VIDEO_X11_DGAMOUSE=0 armyops

My Nvidia drivers are up to date and working well. Direct Rendering is working.  My system is a little low on resources, but the game actually performed well enough to play last week. Since them I've installed Xgl so compiz would work.

Alien arena works just fine, and now I'm not sure what technical information to post that would help you help me! :)

Thank you very much in advance for answering, as I really am not sure where to go from here...

System:
Ubuntu 8.04.1 
GNOME 2.22.3 (Ubuntu 2008-07-09)
Linux 2.6.24-20-generic
i686
AMD Athlon(TM) XP 1800+
376 MB (low, I know, but it was doing OK a week ago!)

Game Play is very jerky and so is sound. I've looked all over the place, and I'm hoping some whizkid will find this post and speak up!
 
Thanks again,

Peragrate

---

