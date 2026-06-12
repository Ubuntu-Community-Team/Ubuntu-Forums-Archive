---
title: "Need Help With Return to castle wolfenstein"
date: 2012-01-16
forum: Gaming &amp; Leisure
---

### Post by Rnegade21 on 2012-01-16
alright so the big problem is that when I start the game the screen goes black, when I press the keys on my keyboard and move my mouse a little the main menu kind of flickers on and off my screen breifly, which renders the game unplayable
I have an ati hd radeon 5700 series card and i am running the newest version of ubuntu

also the sound doesn't work and i know there's a fix for that i just don't remember what

the last time I used this game was on lucid a while back, i dont really remember if i had these problems back then. but i'm hoping someone can help me out.

I know that there are problems running this game on windows with ati cards and there is a fix for that. but i'm not sure about linux

It's the lattest install from the ID website's ftp server, the pkg files are from the platinum edition discs

---

### Post by mastablasta on 2012-01-18
Did you install the ATI proprietary drivers?
 
Try running it from terminal to get the error output.

---

### Post by mateo14 on 2012-01-18
> **Rnegade21 said:**
> alright so the big problem is that when I start the game the screen goes black, when I press the keys on my keyboard and move my mouse a little the main menu kind of flickers on and off my screen breifly, which renders the game unplayable
I have an ati hd radeon 5700 series card and i am running the newest version of ubuntu

also the sound doesn't work and i know there's a fix for that i just don't remember what

the last time I used this game was on lucid a while back, i dont really remember if i had these problems back then. but i'm hoping someone can help me out.

I know that there are problems running this game on windows with ati cards and there is a fix for that. but i'm not sure about linux

It's the lattest install from the ID website's ftp server, the pkg files are from the platinum edition discs

Try bzzwolfsp:

[http://code.google.com/p/bzzwolfsp/](http://code.google.com/p/bzzwolfsp/)

---

### Post by Rnegade21 on 2012-01-19
> **mastablasta said:**
> Did you install the ATI proprietary drivers?
 
Try running it from terminal to get the error output.


yes I installed the fglrx driver from synaptic

I ran wolfenstein fro terminal and got this


rnegade@rnegade-CM6630-CM6730-CM6830:~$ cd /usr/local/games/wolfenstein
rnegade@rnegade-CM6630-CM6730-CM6830:/usr/local/games/wolfenstein$ sudo ./wolfsp[sudo] password for rnegade: 
Wolf 1.41 linux-i386 Dec  4 2002
----- FS_Startup -----
Current search path:
/home/rnegade/.wolf/main
/usr/local/games/wolfenstein/main/sp_pak4.pk3 (21 files)
/usr/local/games/wolfenstein/main/sp_pak3.pk3 (14 files)
/usr/local/games/wolfenstein/main/sp_pak2.pk3 (232 files)
/usr/local/games/wolfenstein/main/sp_pak1.pk3 (1342 files)
/usr/local/games/wolfenstein/main/pak0.pk3 (4775 files)
/usr/local/games/wolfenstein/main

----------------------
6384 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing wolfconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Radeon HD 5700 Series 
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon HD 5700 Series 
GL_VERSION: 2.1 (4.1.11251 Compatibility Profile Context)
GL_EXTENSIONS: gs
GL_MAX_TEXTURE_SIZE: 16384
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
picmip2: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
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

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/usr/local/games/wolfenstein/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xf0e36778  
Sys_LoadDll(ui) succeeded!
Parsing menu file:ui/main.menu
r_rmse of 0.000000 has saved 12kb
Parsing menu file:ui/setup.menu
Parsing menu file:ui/controls.menu
Parsing menu file:ui/cdkey.menu
Parsing menu file:ui/system.menu
Parsing menu file:ui/options.menu
Parsing menu file:ui/credit.menu
r_rmse of 0.000000 has saved 204kb
r_rmse of 0.000000 has saved 252kb
r_rmse of 0.000000 has saved 264kb
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
UI menu load time = 291 milli seconds
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
UI menu load time = 233 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: rnegade-CM6630-CM6730-CM6830
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
RE_Shutdown( 1 )
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 130
  Minor opcode of failed request: 10
  Serial number of failed request: 6412
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

---

### Post by Rnegade21 on 2012-01-19
> **mateo14 said:**
> Try bzzwolfsp:

[http://code.google.com/p/bzzwolfsp/](http://code.google.com/p/bzzwolfsp/)


I read the link and it apaers to be some kind of mod for co-op

---

### Post by mateo14 on 2012-01-20
> **Rnegade21 said:**
> I read the link and it apaers to be some kind of mod for co-op

You can play in standard singleplayer mode of RTCW.

"building linux binaries on linux:

type make

make a folder: /usr/local/games/wolfenstein/
copy wolfsp.i386 and wolfspded.i386 in it, also make a subdirectory called: main
put the produced .so files (cgame, ui and qagame) in this main folder, also copy your *.pk3 files from your original installation into this main folder, then you should be able to start the game with the ./wolfsp.i386 command

running a server is only possible if sv_pure is set to 0


building windows binaries on linux:
install the cross tools

type ./cross-make-mingw.sh

put the exe files in a folder, make a subfolder and put the dll's and the pk3 files in it

running a server is only possible if sv_pure is set to 0

building os x binaries on os x

Make sure the osx 10.5 SDK is installed (its included in xcode 3.x)

type make
type ./make-macosx-ub.sh

copy the wolfsp.app to a folder
copy the dylib files to: /Users/<username>/Library/Application\ Support/Wolfenstein/main
run the app file

running a server is only possible if sv_pure is set to 0
running a dedicated server is only possible from the command line for now"

[http://code.google.com/p/bzzwolfsp/source/browse/trunk/README](http://code.google.com/p/bzzwolfsp/source/browse/trunk/README)

---

