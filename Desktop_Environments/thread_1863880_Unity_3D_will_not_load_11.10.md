---
title: "Unity 3D will not load 11.10"
date: 2011-10-18
forum: Desktop Environments
---

### Post by bullium on 2011-10-18
I just did a fresh install of Ubuntu 11.10 x64 on my desktop, which consists of the following configuration:

Intel Core2 Quad CPU Q6600 @ 2.40GHz
8GB Ram
NVIDIA GeForce 8600 GT/PCI/SSE2 (Dual Monitors)

I've been running this system since 8.04 and have always used the Ubuntu supplied drivers and have always had no issues with 3D support. I did a fresh install of 11.04 when it was released and all my 3D effects and rendering worked without any issues. When 11.10 was released I decided to do another fresh install instead of an upgrade. I'm able to install the (version current) driver from the Additional Drivers and use nvidia-settings to enable Twinview mode so I can use my second monitor. 

I first tried (version 173) but that had issues with nvidia-settings; I saw some other posts here on the Ubuntu forums recommending (version current) so I tried that and it actually allows me to configure my second monitor as I used to. 

Now things start to get interesting. The output from *glxinfo* and *unity_support_test* are conflicting it seems.

Here's the output from */usr/lib/nux/unity_support_test -p*


```
OpenGL vendor string:   NVIDIA Corporation

OpenGL renderer string: GeForce 8600 GT/PCI/SSE2

OpenGL version string:  3.3.0 NVIDIA 280.13



Not software rendered:    yes

Not blacklisted:          no

GLX fbconfig:             yes

GLX texture from pixmap:  yes

GL npot or rect textures: yes

GL vertex program:        yes

GL fragment program:      yes

GL vertex buffer object:  yes

GL framebuffer object:    yes

GL version is 1.4+:       yes



Unity 3D supported:       no


```

Output from */usr/bin/glxinfo*

```
name of display: :0

display: :0  screen: 0

direct rendering: Yes

server glx vendor string: NVIDIA Corporation

server glx version string: 1.4

server glx extensions:

    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 

    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 

    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 

    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 

    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 

    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB

client glx vendor string: NVIDIA Corporation

client glx version string: 1.4

client glx extensions:

    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 

    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 

    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 

    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 

    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 

    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 

    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 

    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 

    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 

    GLX_ARB_create_context_robustness

GLX version: 1.4

GLX extensions:

    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 

    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 

    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 

    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 

    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 

    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 

    GLX_ARB_get_proc_address

OpenGL vendor string: NVIDIA Corporation

OpenGL renderer string: GeForce 8600 GT/PCI/SSE2

OpenGL version string: 3.3.0 NVIDIA 280.13

OpenGL shading language version string: 3.30 NVIDIA via Cg compiler

```

From what I can see my video card has been blacklisted. Why would this video card be blacklisted for Unity when *glxinfo* is telling that direct rendering for my video card is functioning? It seems 3D acceleration is enabled and functioning but Unity 3D simply won't run, due to being blacklisted?

---

### Post by enterdavertex on 2011-10-18
Got a few problems like that one... try reinstaling a oldest driver, that should fix it

---

### Post by bullium on 2011-10-18
> **enterdavertex said:**
> Got a few problems like that one... try reinstaling a oldest driver, that should fix it
I've tried the following drivers with no success on 11.10:
(version 173), (version 96) and (post-release updates) (version 173-updates) and none of those work with the nvidia-settings tool. The only one that seems to work properly is (version current). Some of the one's listed mucked it up so bad that the desktop wouldn't even load...So I'd like to stick with the (version current) if possible.

---

### Post by bullium on 2011-10-19
So the only suggestion is to use another driver that doesn't work for my card?

---

### Post by forestG on 2011-11-18
you could try sudo apt-get install gnome to install gnome 3. It is not that much different from Unity 3d.

---

### Post by mswift on 2011-11-18
Here you go :

[HTML]http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity[/HTML]

---

