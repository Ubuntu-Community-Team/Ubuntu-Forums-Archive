---
title: "Oblivion under Wine using ATI"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by manuelkuhs on 2007-06-23
I've been able to partially get Oblivion running under Wine using [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

I have an ATI Radeon 9550 256MB RAM, using the drivers from Restricted Drivers (Ubuntu 7.04). Native UT2004 works perfectly.

The best results I can get is by turning on Bloom, without Bloom, graphics are completely messed up. Movies also were turned off. Once I get into the game, I get around 1-2 fps :(

This is the first error message I received:

fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1d5ca0) : stub, simulating 256MB for now, returning 256MB left

And then the following repeatedly:

fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870913: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483649: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."

So my nOOb conclusion is that my Video graphics memory is not being recognised/utilised by Wine :(

---

### Post by PartisanEntity on 2007-06-23
Please post only 1 thread per issue.

[http://ubuntuforums.org/showthread.php?t=482026](http://ubuntuforums.org/showthread.php?t=482026)

---

