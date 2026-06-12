---
title: "Oblivion under Wine using ATI"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by manuelkuhs on 2007-06-23
I've been able to partially get Oblivion running under Wine using [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

I have an ATI Radeon 9550 256MB RAM, using the drivers from Restricted Drivers. Native UT2004 works perfectly.

The best results I can get is by turning on Bloom, without Bloom, graphics are completely messed up. Movies also were turned off. Once I get into the game, I get around 1-2 fps :(

This is the first error message I received:

fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1d5ca0) : stub, simulating 256MB for now, returning 256MB left

And then the following repeatedly:

fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870913: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483649: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."

So my nOOb conclusion is that my Video graphics memory is not being recognised/utilised by Wine :(

Anyone have any idea how I can check whether this is the problem?

---

### Post by Cappy on 2007-06-23
Oblivion doesn't work with ATI cards. Sorry. It's in that wiki.

---

### Post by vem0m on 2007-06-23
> **Cappy said:**
> Oblivion doesn't work with ATI cards. Sorry. It's in that wiki.

Not true it can run if you work to disable shaders tho for manuelkuhs he shouldn't try running it in windows let alone linux using a 9550 i mean hell thats an old card it wouldn't handle it to begin with best bet upgrade to a newer card :)

---

### Post by Enverex on 2007-06-24
> **manuelkuhs said:**
> So my nOOb conclusion is that my Video graphics memory is not being recognised/utilised by Wine :(

No, Wine has no way of probing your video RAM so you have to manually set it in regedit, it doesn't mean it's using 256MB of system RAM or anything.

But Oblivion really isn't up to par in Wine at the moment. The engine didn't run all that well on Windows so running it in Wine with an old card (and ATi of all things) is just going to be a disaster.

---

