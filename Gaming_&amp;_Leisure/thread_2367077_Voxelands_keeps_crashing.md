---
title: "Voxelands keeps crashing"
date: 2017-07-25
forum: Gaming &amp; Leisure
---

### Post by dommel2002 on 2017-07-25
Recently downloaded Voxelands 1704.00 via the tarball proposed on [I][http://forum.voxelands.com/viewtopic.php?id=829](http://forum.voxelands.com/viewtopic.php?id=829)
[/I]I extracted it into the home folder (after renaming it 'voxelands') and then edited it with the following commands:

```

$ cd voxelands
~/voxelands$ cmake . -DRUN_IN_PLACE=1
~/voxelands/bin$ make -j2 install

```

but when I rebooted and finally opened the game with:

```

$ cd voxelands
~/voxelands$ cd bin
~/voxelands$ ./voxelands

```

it crashed after a few seconds and I got this output:

```

~/voxelands/bin$ ./voxelands
signal_handler_init()
Using relative paths (RUN_IN_PLACE)
path_data = /home/dominic/voxelands/data
path_configdata = /home/dominic/voxelands
path_userdata = /home/dominic/voxelands
Debug streams initialized, disable_stderr=0
21:13:59: ACTION[main]: voxelands with SER_FMT_VER_HIGHEST=21, VER=1704.00 RUN_IN_PLACE=1 USE_GETTEXT=1 INSTALL_PREFIX=/usr/local BUILD_TYPE=Release
INFO: Initial run of init_mapnode with g_texturesource=NULL. If this segfaults, there is a bug with something not checking for the NULL value.
Irrlicht Engine version 1.8.3
Linux 4.10.0-27-generic #30~16.04.2-Ubuntu SMP Thu Jun 29 16:07:46 UTC 2017 x86_64
Using renderer: OpenGL 3.0
Gallium 0.4 on AMD RS880 (DRM 2.49.0 / 4.10.0-27-generic, LLVM 3.8.0): X.Org
OpenGL driver version is 1.2 or better.
GLSL version: 1.3
Loaded texture: /home/dominic/voxelands/data/textures/menulogo.png
INFO: Full run of init_mapnode with g_texturesource!=NULL
Loaded texture: /home/dominic/voxelands/data/textures/mud.png
Loaded texture: /home/dominic/voxelands/data/textures/stone.png
Loaded texture: /home/dominic/voxelands/data/textures/grass_side.png
INFO: Full run of init_mapnode with g_texturesource!=NULL
AuthManager: loading from /home/dominic/voxelands/world/auth.txt
BanManager: loading from /home/dominic/voxelands/world/ipban.txt
21:15:36: ACTION[ServerThread]: dominic joins game. List of players: dominic 
Clouds::Clouds(irr::scene::ISceneNode*, irr::scene::ISceneManager*, irr::s32, irr::u32)
Loaded texture: /home/dominic/voxelands/data/textures/sun.png
Loaded texture: /home/dominic/voxelands/data/textures/moon.png
CHAT: # Server: version=1704.00, uptime=0.3, clients={dominic,}
CHAT: *** dominic joined game
Loaded texture: /home/dominic/voxelands/data/textures/ringbg.png
Loaded texture: /home/dominic/voxelands/data/textures/progress_ring.png
Loaded texture: /home/dominic/voxelands/data/textures/inventory.png
Loaded texture: /home/dominic/voxelands/data/textures/heart.png
Loaded texture: /home/dominic/voxelands/data/textures/body_feet.png
Loaded texture: /home/dominic/voxelands/data/textures/body_lleg.png
Loaded texture: /home/dominic/voxelands/data/textures/body_rleg.png
Loaded texture: /home/dominic/voxelands/data/textures/body_torso.png
Loaded texture: /home/dominic/voxelands/data/textures/body_hands.png
Loaded texture: /home/dominic/voxelands/data/textures/body_larm.png
Loaded texture: /home/dominic/voxelands/data/textures/body_rarm.png
Loaded texture: /home/dominic/voxelands/data/textures/body_head.png
Loaded texture: /home/dominic/voxelands/data/textures/crosshair_unfocused.png
**Segmentation fault (core dumped)**

```

Can anyone help me?

---

