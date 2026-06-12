---
title: "Nvidia problems"
date: 2020-08-13
forum: Gaming &amp; Leisure
---

### Post by heikki-kniivila on 2020-08-13
Hello.

I just bought a new laptop (Asus rog strix G731GT) that has intel AND nvidia (GeForce GTX 1650 Mobile / Max-Q) display adapters.
ok, i got them both working, currently using the nvidia one. i can switch from the Nvidia tool.

But the problem is that my ~7 years old laptop (HP ProBook 455 G1) that only had one weak integrated amd gpu, runs games and videos better than my new laptop.

Any ideas on where to dig info?

glxgears gives me 30029 frames in 5.0 seconds = 6005.629 FPSbut i can see the gears refreshing poorly.

I am playing Cities:Skylines with Steam, and when i move the map, it refreshes very poorly also. Looks like some vertical lines, like it refreshes part of the screen and not the other part.

Any ideas on how to fix this crap?[INDENT]$ glxinfo |grep -i -e nvidia -e intel -e rendering


direct rendering: Yes
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL core profile version string: 4.6.0 NVIDIA 450.57
OpenGL core profile shading language version string: 4.60 NVIDIA
    GL_NV_path_rendering, GL_NV_path_rendering_shared_edge, 
    GL_NV_stereo_view_rendering, GL_NV_texgen_reflection, 
OpenGL version string: 4.6.0 NVIDIA 450.57
OpenGL shading language version string: 4.60 NVIDIA
    GL_NV_path_rendering, GL_NV_path_rendering_shared_edge, 
    GL_NV_stereo_view_rendering, GL_NV_texgen_reflection, 
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 450.57
    GL_NV_packed_float_linear, GL_NV_path_rendering, 
    GL_NV_path_rendering_shared_edge, GL_NV_pixel_buffer_object, 
    GL_NV_shadow_samplers_cube, GL_NV_stereo_view_rendering, 




[/INDENT]
Thanks,
Edit: Sorry, forgot to mention, i have Ubuntu 20.04.1 and all upgraded. Just did a fresh install.

---

### Post by mastablasta on 2020-08-13
how do you know that you are running the games on nvidia? there are some issues with switching in 20.04 i believe. what driver (version) are you using? perhaps nvidia driver has the issues. if you switched to it it should work well. GTX1650 has been arrund for a while but maybe mobile version is relatively new as i've seen some users having issues with it.

glxgears is not reliable source. if you want to test and compare you can use phoronix test suite and use one of the demos there to test and compare.

---

### Post by math492m on 2020-08-18
sounds like a driver problem to me  

have you changed from intigrated graphics ??

---

### Post by heikki-kniivila on 2020-08-22
yes, i have switched from intel graphis to nvidia.
in the nvidia settings on the section PRIME Profiles, i have 3 options:
"NVIDIA (Performance Mode)"
"NVIDIA On-Demand"
"Intel" (Power Saving Mode)

And i have set the  "NVIDIA (Performance Mode)"

and if i look at glxinfo, i will get NVIDIA text there, and if i switch to intel, i see the INTEL text, so yes, it is using NVIDIA.

My driver version is  450.57
also tried 440 series of driver with no success.

---

### Post by heikki-kniivila on 2020-08-22
And also i know it is using the NVIDIA device, because if i switch to intel and start Liftoff drone game, it is like 4-7 FPS and with nvidia it is a lot better.
so the problem seems to be with cities skylines, not really with liftoff.

---

### Post by mastablasta on 2020-08-23
in that case troubleshoot with the city skylines.

i bought an old game Total war: Medieval. it has really bad FPS already in menu later it gets even worse. looks like some sort of software rendering even though the game recognises the card and sets all settings to high using auto detect. i havent managed to resolve it yet. i can play most older games with no issues (CS:GO, left4 dead, Far cry 2...) but not this one. if only one game is the issue then it is best to trouble shoot with its developer/publisher or whoever guarantees the game works on certain machine.

---

