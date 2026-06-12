---
title: "Yo Frankie (open source blender game) does not play."
date: 2009-05-28
forum: Gaming &amp; Leisure
---

### Post by Periswell on 2009-05-28
Hello

*i posted this on the blenderartist forum but it was not replied too, i think its something to do with my computer and not the game*

I have just downloaded Yo Frankie but it does not work. I am on Ubuntu (yes linux) 8.10 so i ran the yofrankie-linux-i386 file. The start animation and the menu works, controls works too but when i press play it crashes and closes. In the terminal it looks like this:
Quote:
joshua@joshua-laptop:~$ '/home/joshua/blender_game_engine/yofrankie-linux-i386' argv[0] = '/home/joshua/blender_game_engine/yofrankie-linux-i386'
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Detected GL_ARB_multitexture
Detected GL_ARB_shader_objects
Detected GL_ARB_vertex_shader
Detected GL_ARB_fragment_shader
Detected GL_ARB_vertex_program
Detected GL_ARB_depth_texture
Detected GL_EXT_separate_specular_color
read library: lib //../chars/butterfly.blend
Warning, sensor "menu_delay" has lost a link to a controller (link 2 of 3) from object "menu_logic"
possible causes are partially appended objects or an error reading the file,logic may be incorrect
Warning, sensor "menu_delay" could not find its controller (link 3 of 3) from object "menu_logic"
there has been an error converting the blender controller for the game engine,logic may be incorrect
Warning, sensor "sensor2" has lost a link to a controller (link 1 of 1) from object "butterfly_logic"
possible causes are partially appended objects or an error reading the file,logic may be incorrect
read library: lib //../props/pickups.blend
read library: lib //../chars/butterfly.blend
read library: lib //../props/plants.blend
read library: lib //../props/flowers.blend
read library: lib //../props/trees.blend
read library: lib //../chars/frankie.blend
read library: lib //../props/fences.blend
read library: lib //../props/platforms.blend
read library: lib //../props/rocks.blend
read library: lib //../hud/hud.blend
read library: lib //../effects/fx_blast.blend
read library: lib //frankie_actions.blend
read library: lib //momo_actions.blend
yofrankie-linux-i386: shader/slang/slang_codegen.c:2442: _slang_gen_var_decl: Assertion `!is_sampler_type(&var->type)' failed.
Aborted
joshua@joshua-laptop:~$
It also crashes in blender. Does anyone know how to fix this error? Thanks in advance.

-joshua

---

### Post by Dedoimedo on 2009-05-28
Are you using an onboard graphics card? Yo Frankie needs a good one with 3D shaders. For instance, I can't run it on my aging T42 with an older card.
Dedoimedo

---

### Post by Periswell on 2009-05-28
don't worry, i just got a post on the blender artist forum saying that all i had to do is turn off the shaders, and now it works. thanks anyway.

-joshua

---

### Post by Sealbhach on 2009-05-28
Works fine for me in Jaunty 64-bit, just for info.

.

---

### Post by olmecnz on 2009-05-28
How to go about switching of the shaders? I could not see a config file.... Do I have to have blender installed (maybe stupid question)

---

### Post by Sealbhach on 2009-05-28
> **olmecnz said:**
> How to go about switching of the shaders? I could not see a config file.... Do I have to have blender installed (maybe stupid question)

It's in the Options screen when you start up the game.

.

---

### Post by gstephen on 2012-10-01
What if it really didn't start because blender crashes.?

---

### Post by Statia on 2012-11-12
Yo Frankie has never worked for me.
I just tried again and reinstalled it. Since trying it last I have a newer kernel, newer nvidia driver, newer kwin.
Result remains the same as ever:

```
TexFace Convert: Material "Material.TF.1026" created.
Warning: material "signpost_bolts" skipped - to convert old game texface to material go to the Help menu.
Segmentation fault (core dumped)
```

And looking here:
[http://www.yofrankie.org/about-apricot/](http://www.yofrankie.org/about-apricot/)
I see I am not the only one.

I blame it on the shoddy QA so typical of FOSS.

---

