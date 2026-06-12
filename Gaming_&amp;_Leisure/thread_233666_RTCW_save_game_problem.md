---
title: "RTCW save game problem"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by eBait~ on 2006-08-10
Well, I succesfully installed RTCW with my Windows data. No problem. Online, no problem. Offline mission, problem.
It tells me that It can't write a savefile, some terminal output:
```

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
picmip2: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
ATI truform: disabled
NV distance fog: disabled
Initializing Shaders
...loading 'scripts/ai.shader'
...loading 'scripts/alpha.shader'
...loading 'scripts/blacksmokeanim.shader'
...loading 'scripts/blacksmokeanimb.shader'
...loading 'scripts/characters.shader'
...loading 'scripts/clipboard.shader'
...loading 'scripts/common.shader'
...loading 'scripts/cursorhints.shader'
...loading 'scripts/decals.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/expblue.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/fijets.shader'
...loading 'scripts/firest.shader'
...loading 'scripts/flamethrower.shader'
...loading 'scripts/funnel.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/heat.shader'
...loading 'scripts/lights.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/maxx.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/metal.shader'
...loading 'scripts/models.shader'
...loading 'scripts/netest.shader'
...loading 'scripts/oldwolf.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/particle.shader'
...loading 'scripts/q3view.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/signs.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/solo.shader'
...loading 'scripts/surfaces.shader'
...loading 'scripts/terrain.shader'
...loading 'scripts/test.shader'
...loading 'scripts/twiltb.shader'
...loading 'scripts/twiltb2.shader'
...loading 'scripts/ui.shader'
...loading 'scripts/ui_hud.shader'
...loading 'scripts/ui_notebook.shader'
...loading 'scripts/ui_wolf.shader'
...loading 'scripts/viewflames.shader'
...loading 'scripts/walls.shader'
...loading 'scripts/z_light.shader'
----- finished R_Init -----
Sys_LoadDll(/usr/local/games/wolfenstein/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa79d3778
Sys_LoadDll(ui) succeeded!
Parsing menu file:ui/main.menu
r_rmse of 0.000000 has saved 864kb
Parsing menu file:ui/setup.menu
Parsing menu file:ui/controls.menu
Parsing menu file:ui/cdkey.menu
Parsing menu file:ui/system.menu
Parsing menu file:ui/options.menu
Parsing menu file:ui/credit.menu
r_rmse of 0.000000 has saved 1056kb
r_rmse of 0.000000 has saved 1104kb
r_rmse of 0.000000 has saved 1116kb
Parsing menu file:ui/connect.menu
Parsing menu file:ui/quit.menu
Parsing menu file:ui/vid_restart.menu
Parsing menu file:ui/snd_restart.menu
Parsing menu file:ui/rec_restart.menu
Parsing menu file:ui/default.menu
Parsing menu file:ui/error.menu
Parsing menu file:ui/serverinfo.menu
Parsing menu file:ui/quitcredit.menu
Parsing menu file:ui/resetscore.menu
Parsing menu file:ui/buy_pop.menu
Parsing menu file:ui/multiplayer_pop.menu
Parsing menu file:ui/play.menu
Parsing menu file:ui/load.menu
Parsing menu file:ui/mods.menu
Parsing menu file:ui/briefing.menu
UI menu load time = 1658 milli seconds
Parsing menu file:ui/ingame.menu
Parsing menu file:ui/ingame_controls.menu
Parsing menu file:ui/ingame_options.menu
Parsing menu file:ui/ingame_system.menu
Parsing menu file:ui/ingame_leave.menu
Parsing menu file:ui/ingame_player.menu
Parsing menu file:ui/ingame_load.menu
Parsing menu file:ui/ingame_save.menu
Parsing menu file:ui/in_vid_restart.menu
Parsing menu file:ui/in_snd_restart.menu
Parsing menu file:ui/in_rec_restart.menu
Parsing menu file:ui/notebook.menu
Parsing menu file:ui/clipboard.menu
Parsing menu file:ui/bookz.menu
Parsing menu file:ui/bookv.menu
Parsing menu file:ui/bookp.menu
Parsing menu file:ui/pregame.menu
Parsing menu file:ui/test.menu
Parsing menu file:ui/ingame_help.menu
UI menu load time = 1633 milli seconds
Couldn't write wolfconfig.cfg.
Couldn't write main.
----- CL_Shutdown -----
RE_Shutdown( 1 )
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 135
  Minor opcode of failed request: 10
  Serial number of failed request: 94
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```
[b]Couldn't write wolfconfig.cfg.
Couldn't write main.[/b], that's it. The complete wolfenstein has got an chmod 777 -R, so all is writable.
Cheers,

---

### Post by Cyorxamp on 2006-08-12
I've just had precisely the same thing happen to me :S

Good old google brought us together... anyone know how to solve this?

---

### Post by hexion on 2006-08-12
Same here.

It's because you have data in a fat32 partition. Possibly mounted as root (if auto option in the fstab)

Execute it with sudo:

> sudo et

It will work

---

### Post by Cyorxamp on 2006-08-12
Ok sure I have a FAT32 partition mounted in my fstab...

How does that affect RTCW?

Whats 'sudo et' ?

I'm just not following what you're trying to say.

---

### Post by HAARP on 2006-08-12
This config should be in your home folder, not your game folder
/home/whoever/.wolf
Press ctrl+h in nautilus to display files&folders beginning with a dot.
What about thsi folder and it's subfolders? Do you have the right permissions?

---

### Post by hexion on 2006-08-12
"sudo" command lets execute next argument as a superuser (asking you for a password).

"sudo et" launches Enemy Territory with superuser privileges, so it will let you write your config.

A better solution, like HAARP say, is to change the folder owner of .etwolf

Instead of "sudo et", try this:

Open a terminal and write:
> 
cd
chown -R user:user .etwolf/

**change "user" for your username** i.e.) hexion:hexion

Then try to launch Enemy Territory again. It should work (if it doesn't, try sudo command)

---

### Post by Cyorxamp on 2006-08-12
Problem solved...

When you've used the RTCW installer and copied the needed pak files... you need to run wolfsp as root (i.e. sudo wolfsp) for it to actually fill the '.wolf' directory (thats right of 'cyorxamp' not root, even tho you're running as root - it's bizzare).

After you've ran it as root... do the usual 'sudo chown cyorxamp -R ~/.wolf'

Run normally from then on and it should work,

I have these lousy installers - but I guess it's better than none at all.

---

