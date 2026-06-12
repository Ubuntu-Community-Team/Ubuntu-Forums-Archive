---
title: "Eternal Lands won't run?"
date: 2011-04-26
forum: Gaming &amp; Leisure
---

### Post by btbgeek on 2011-04-26
When I launch Eternal lands it crashes.
Clicking in the games folder produces this in an error window.

[INDENT]
This information about your graphic hardware and software may help.
Output from "lspci | grep -i vga":
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
Output from "glxinfo | head -5":


The following is your error log contents.  Note it is overwritten each time you run the game.



Log started at 2011-04-26 13:08:06 localtime (EDT)

[13:08:06] Using the server profile: main
[13:08:06] Window size adjusted to 1014x713
[13:08:07] GL_ARB_multitexture extension found, using it.
[13:08:07] GL_EXT_compiled_vertex_array extension found, using it.
[13:08:07] GL_ARB_point_sprite extension found, using it.
[13:08:07] GL_ARB_texture_compression extension found, using it.
[13:08:07] Couldn't find the GL_EXT_texture_compression_s3tc extension, not using it...
[13:08:07] GL_SGIS_generate_mipmap extension found, using it.
[13:08:07] GL_ARB_shadow extension found, using it.
[13:08:07] GL_ARB_vertex_buffer_object extension found, using it.
[13:08:07] GL_EXT_framebuffer_object extension found, using it.
[13:08:07] GL_EXT_draw_range_elements extension found, using it.
[13:08:07] GL_ARB_texture_non_power_of_two extension found, using it.
[13:08:07] GL_ARB_fragment_program extension found, using it.
[13:08:07] GL_ARB_vertex_program extension found, using it.
[13:08:07] GL_ARB_fragment_shader extension found, using it.
[13:08:07] GL_ARB_vertex_shader extension found, using it.
[13:08:07] GL_ARB_shader_objects extension found, using it.
[13:08:07] GL_ARB_shading_language_100 extension found, using it.
[13:08:07] GL_ARB_texture_mirrored_repeat extension found, NOT using it...
[13:08:07] GL_ARB_texture_rectangle extension found, NOT using it...
[13:08:07] GL_EXT_fog_coord extension found, NOT using it...
[13:08:07] Couldn't find the GL_ATI_texture_compression_3dc extension, not using it...
[13:08:07] Couldn't find the GL_EXT_texture_compression_latc extension, not using it...

This was the program output:  Note it is overwritten each time you run the game.
[/INDENT]

Running in terminal with "sudo ./el.x86_64.linux.bin" results in "segmentation fault"

Any Ideas?

---

### Post by LinXNut on 2011-04-26
I have had the same problem before with that game...The problem I had was that my graphics card was too old. "Segmentation Fault" can be a number of issues...

Im sorry I cant provide too much info...:(

---

### Post by btbgeek on 2011-04-27
I figured it out. 
If anyone else has this problem try:
```
cd /usr/share/games/eternallands
mv shaders shaders-bak
```

The shaders are broken, moving them fixes it!

Brian

---

### Post by pjbroad on 2011-04-29
Just to clarify, the shaders are broken for your graphics card and/or drivers.  That's a shame but the shaders work for the vast majority of users.  I'm glad you manage to find a work around.  Please could you let us know which graphics card and drivers version you are using.  Perhaps something can be done to fix the problems. For information, you can get lots of help on the Eternal Lands official forums at [http://www.eternal-lands.com/forum/](http://www.eternal-lands.com/forum/).

---

