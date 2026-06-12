---
title: "PyOpenGL APP + GLXgears problem un kubuntu 5.04"
date: 2005-04-08
forum: Desktop Environments
---

### Post by tsubasa on 2005-04-08
Hello :) 

I have a litte problem with the last kubuntu,

I use the 686 kernel on athlon xp 2800+ 2.6.10 and i have very low fps in glxgears and all pyopengl software.

I have generally between 2700 and 2900 fps in glxgears with the drivers 71.74 from nvidia and see now:

tsubasa@mastor:~$ glxgears
47 frames in 5.0 seconds =  9.400 FPS
48 frames in 5.0 seconds =  9.600 FPS
48 frames in 5.0 seconds =  9.600 FPS
49 frames in 5.0 seconds =  9.800 FPS
46 frames in 5.0 seconds =  9.200 FPS
48 frames in 5.0 seconds =  9.600 FPS
49 frames in 5.0 seconds =  9.800 FPS
49 frames in 5.0 seconds =  9.800 FPS
49 frames in 5.0 seconds =  9.800 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
tsubasa@mastor:~$ 

This my glxinfo:

tsubasa@mastor:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5600/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.74

 
In PyopenGl Apps it the same problem : /  i have very low fps but game like quake 3 / cedega steam works well .

thanks for your help

---

### Post by tsubasa on 2005-04-09
Resolve by switching from 686 kernel to 386 kernel.

Does Barton Xp 2800 + support 686 kernel ?

---

