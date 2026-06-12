---
title: "Yo Frankie error"
date: 2009-06-27
forum: Gaming &amp; Leisure
---

### Post by analyzer on 2009-06-27
Hello together

I downloaded “yo Frankie“ from [http://www.yofrankie.org/download/](http://www.yofrankie.org/download/). The game starts but the screen keeps gray. There are some error messages on the shell.

```
./yofrankie-linux-i386 
guessing './yofrankie-linux-i386' == '/media/disk/Spiele/blender_game_engine/./yofrankie-linux-i386'
argv[0] = './yofrankie-linux-i386'
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Detected GL_ARB_multitexture
Detected GL_ARB_vertex_program
Detected GL_ARB_depth_texture
Detected GL_EXT_separate_specular_color
shaders not supported!
No CDROM devices available
read library: lib //../chars/butterfly.blend
shaders not supported!
No CDROM devices available
Warning, sensor "menu_delay" has lost a link to a controller (link 2 of 3) from object "menu_logic"
	possible causes are partially appended objects or an error reading the file,logic may be incorrect
Warning, sensor "menu_delay" could not find its controller (link 3 of 3) from object "menu_logic"
	there has been an error converting the blender controller for the game engine,logic may be incorrect
Warning, sensor "sensor2" has lost a link to a controller (link 1 of 1) from object "butterfly_logic"
	possible causes are partially appended objects or an error reading the file,logic may be incorrect
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_plain
	mouseover: mouse ob name is wrong OBbutterfly_plain
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
	mouseover: mouse ob name is wrong OBbutterfly_logic
Mesa 7.4 implementation error: Unable to delete texture, no context
Please report at bugzilla.freedesktop.org

```

I use the RadeonHD driver in Version 1.2.5 and an ATI Mobility Radeon X300 graphic adapter. Ubuntu 9.04

Thanks.

---

### Post by hessiess on 2009-06-27
YoFrankie was created with Blender game engine, which is well known for having problems with ATI hardwere. All I can sugest is that you disable compiz and upgrade the drivers(if possable).

---

### Post by analyzer on 2009-06-27
> **hessiess said:**
> YoFrankie was created with Blender game engine, which is well known for having problems with ATI hardwere. All I can sugest is that you disable compiz and upgrade the drivers(if possable).

Thanks for your reply. Compiz is disabled and the driver is already up to date.

---

### Post by dingheim on 2011-11-26
I downloaded the game from Ubuntu Repositories on two separate machines which have different graphic configurations.  One is a laptop with Intel Mobility Chipset 4 series, and the other is a Dell Desktop with a ATI Radoen X1600.  It doesn't work on either of them and the failure is similar.  The failure seems like a timing issue that causes the menu not to displayed, because, on the title screen, an icon and a faint outline of a menu appears and disappears very fast leaving the clouds, some faint structures at the bottom, and a small music score looping continuously.

I don't how useful this is but it seems yofrankie.org is offline as of 1:30 AM -8 GMT on 11/26/11.

---

