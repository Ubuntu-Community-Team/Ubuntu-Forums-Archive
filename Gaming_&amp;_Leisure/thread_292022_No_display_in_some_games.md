---
title: "No display in some games"
date: 2006-11-03
forum: Gaming &amp; Leisure
---

### Post by Sukarn on 2006-11-03
I am using Edgy Eft, completely up to date. The problem I am having is quite weird because the games I am going to tell about were working fine a few days ago but suddenly stopped working.

If I launch [Finity Flight II](http://www.ubuntuforums.org/showthread.php?t=284078) (episode one or two) I get a completely black window. A few days ago the game ran just fine. Running from terminal has no output in the terminal, but the same thing happens. While running, the window is completely black, the CPU usage shoots up to 88% and above, clicking on 'X' to close the window does not do anything (even the force close window option does not appear), pressing Ctrl+C on the terminal window does not do anything. Only way I know of closing it is by going into System Monitor and killing ff2 from there or by closing the terminal window (if run from terminal).

Screenshot of ff2 -
[IMG]http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu/Screenshot-ff2-2.png[/IMG]

Notice the blue bar full at the top right? It shows full CPU usage.

The same thing is happening with Emilia Pinball. The difference is that pinball is not taking up any CPU usage and I get an output in console mode.

Screenshot of Emilia Pinball -
[IMG]http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu/Screenshot-EmiliaPinball.png[/IMG]

Notice the leftmost bar at the top right is empty? It shown almost no CPU usage.

Output -
```
Couldn't open config file: /home/sukarn/.emilia/pinball
Using default values
Initing SDL

0 joysticks were found.
Vendor     : NVIDIA Corporation
Renderer   : unknown board/AGP/SSE/3DNOW!
Version    : 1.5.8 NVIDIA 96.25
Extensions : GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 

SDL_GL_RED_SIZE: 8
SDL_GL_GREEN_SIZE: 8
SDL_GL_BLUE_SIZE: 8
SDL_GL_DEPTH_SIZE: 24
SDL_GL_DOUBLEBUFFER: 1

open /dev/sequencer: No such file or directory
Opened audio at 22050 Hz 16 bit stereo

```

Neverball and Neverputt don't have a completely black screen, some things show up in them.
Screenshots (with terminal output) -

Neverball -
[IMG]http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu/Screenshot-Neverball.png[/IMG]

Neberputt -
[IMG]http://i141.photobucket.com/albums/r43/Sukarn/Ubuntu/Screenshot-Neverputt.png[/IMG]



All other games that I have (like are supertux, barrage) are working fine.
Does anyone have any idea what might be wrong with my system?

---

### Post by curvedinfinity on 2006-11-03
I'ld bet you SDL_image did an update that wasn't very backwards compatible. It sounds to me like the games are working perfectly, but the textures aren't loading. And I think all of the above games (FF2 for sure) use SDL_image to load their images.

See if installing an older version of SDL_image solves the problem. :)

---

### Post by Sukarn on 2006-11-05
Any idea how I can get an older version of SDL_image? I'm completely lost as to how to get an  older version of a package (from the repos).

---

### Post by Sukarn on 2006-11-08
*bump*

Can anyone please tell me how to get an older version of SDL_image?

---

### Post by hikaricore on 2006-11-08
Load synaptic package manager (if you use gnome) or adept (for kde) in your system's administration configuration menu.  And do a search for **sdl-image**.  Now I can't give you the kde full walkthrough as I don't have a kde system in front of me right now, but I will tomorrow at work if needed.  But you should be able to basicly follow the same instructions by adapting them for the UI.  :)  So hopefully for everyone's sanity you have gnome hehe.

Anyway moving on:

After you locate the package right click on it and choose properties and see on the version tab, what versions are availible.  If there's a previous version that is **NOT** for dapper, follow the directions at the bottom of this box to install the previous version.  However if you only see your version listed, you'll need to do a little searching.

sadly searching the edgy package database only brings up what I'm guessing is your current version 1.2.5-2

[http://packages.ubuntu.com/edgy/libs/libsdl-image1.2](http://packages.ubuntu.com/edgy/libs/libsdl-image1.2)

so you'll need to search around and see if you can find a previous version prior to that release.  But personally I don't remember ever upgrading sdl-image on any of the systems I work on.

So this leaves me at a bit of a dead end.

You may want ot check in your package manager (assuing synaptic) in the File menu choose the history option and look through it to find recent upgrades, if you find something that looks similar you may need to follow the steps to downgrade this package with the force version method.

My only guess at this point is you are using non standard sources that have non-ubuntu libraries and you upgraded from one of them.

Hope this sheds some light on your issue, and sorry I couldn't be more helpful.

--Aaron

---

### Post by Sukarn on 2006-11-24
I got a new motherboard with a 64 bit processor, so I reinstalled the OS with amd64 alternate disk.

The issue is now gone (I have to still get a new graphics card, via seems kind of unsupported)

---

### Post by Perfect Storm on 2006-11-24
If you want a good and not so expensive GF card, I can recommend the 6600GT 256mb serie. If you're luck you can get it for under $90

---

### Post by Sukarn on 2006-11-26
I was thinking of getting a GF 7300 GT, costing me about $160.
I already asked my vendor for it today, and since the shop was closed today he told me he'll order it tomorrow and it will arrive by Wed or Thursday.
Is my choice ok or is 6600GT a better card?

---

### Post by Perfect Storm on 2006-11-26
7300 GT is a good choice if you have the money for it :)

---

### Post by Sukarn on 2006-11-26
OK, so 7300GT it is, as I won't be getting a new graphics card again for at least 3 years now.
Thanks for helping with the choice.

---

### Post by mattman on 2006-12-05
I'm having the same problem as the original poster and was wondering if anybody might have a fix for this. I've got an integrated Geforce4 mx440.

---

### Post by Sukarn on 2006-12-07
I had the same card (GeForce 4 MX 440) at the time of making this thread.


Did you by any chance install frozen-bubble 2 through some .debs?

I just found out the one of those debs had a modified SDL file, and that might be the reason for this issue to happen.

I am using 64 bit Feisty, so cannot really test that issue now

---

### Post by mattman on 2006-12-07
The only game I have installed thats not from the repos is Quake3. Other than that I'm running a fairly clean Edgy. I used the Envy script to install the Nvidia 9629 driver and I have Beryl installed but I don't use it because most windows are black when opened.

---

### Post by Sukarn on 2006-12-08
Well, I cannot really help you out then.
GeForce4 MX 440 might be quite a low end card, but it ran beryl fine for me, though some effects like burn were very slow, the rest was quite smooth. I had black windows after opening a lot of windows (like more than 6) at the same time.
I have to say though, I had given my card 64 MB shared memmory, so that might be what raised the number of windows.

---

### Post by mattman on 2006-12-08
I've also given my card 64MB shared memory. I don't think that the nvidia driver is the problem because the driver that was originaly in the Edgy repo didn't even work. Maybe I'll try out Feisty and see if that fixes it.

---

### Post by Sukarn on 2006-12-09
I don't think you should go for Feisty if you want to "fix" things. Feisty is  alpha right now. Breakage is sure to come (I am already facing some breakage)

---

### Post by mattman on 2006-12-09
Good advice. I didn't really think that through. Got any other suggestions?:-D

---

